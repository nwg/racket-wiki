
```racket
#lang racket/base
(require 2htdp/universe 2htdp/image lang/posn)
; The gravitational constant G
(define G 6.67428e-11)

; Assumed scale: 100 pixels = 1AU
(define AU (* 149.6e6 1000))
(define SCALE (/ 250 AU))

;Structure of body;position in m, vector in m/s, mass in kg, radius in m
(struct body (id px py vx vy mass radius color) #:mutable #:transparent) 


;Calculate the force of attraction
(define (force g mass otherMass distance) 
  (/ (* g (* mass otherMass)) (expt distance 2)))

;Calculate direction of the force
(define (directionOfForce dx dy force) 
  (let ([theta (atan dy dx)])
    (list (* (cos theta) force) (* (sin theta) force))))

;Creates a vector to adjust planet heading depending on all other bodies 
(define (attraction body otherBody) 
  (let* ([dx (- (body-px otherBody) (body-px body))]
         [dy (- (body-py otherBody) (body-py body))]
         [distance (sqrt (+ (expt dx 2) (expt dy 2)))]) ;Distance between bodys
    (if (= distance 0) (print "Hitt!")
        (directionOfForce dx dy
                          (force G (body-mass body) (body-mass otherBody) distance)))))

(define timestep (* 12 3600)) ;Half a day

;Creates a list of vectors, a vector for every body
(define (totalAttraction body bodies fxy) 
  (if (equal? bodies '())
      fxy
      (totalAttraction body (cdr bodies) (map + fxy (attraction body (car bodies))))))

;; gravity
;; bodies ⇒ bodies
(define (gravity bodies timestep)
  (let* ([forces (for/list ([b bodies]) (totalAttraction b (remove b bodies) '(0 0)))]
         [vectors
          (for/list ([f forces][b bodies])
            (list (+ (body-vx b) (* (/ (car f) (body-mass b)) timestep))
                  (+ (body-vy b) (* (/ (car(cdr f)) (body-mass b)) timestep))))]
         [positions
          (for/list ([v vectors][b bodies])
            (list (+ (body-px b) (* (car v) timestep))
                  (+ (body-py b) (* (car (cdr v)) timestep))))])
    (for/list ([b bodies][v vectors][p positions])
      (body (body-id b) (car p) (car(cdr p)) (car v) (car(cdr v))
            (body-mass b) (body-radius b) (body-color b)))))

;(struct body (id px py vx vy mass radius color)) ;just a reminder of the struct

;A list of bodies, size of planets is not real... you woldent se the planets. 
(define testCollPlanets
  (list
   (body "Sun" 0 0 0 0 (* 1.98892 (expt 10 30)) 100 "yellow")
   (body "Mercury" (* -0.387098 AU) 0 0 (* -47.362 1000) (* 3.3011 (expt 10 23)) 4 "red")
   (body "Venus" (* 0.723 AU) 0 0 (* 35.02 1000) (* 4.8685 (expt 10 24)) 8 "brown")
   (body "Earth" (* -1 AU) 0 0 (* -29.783 1000) (* 5.9742 (expt 10 24)) 8 "green")
   (body "Mars" (* -1.5236 AU) 0 0 (* -24.077 1000) (* 6.4174 (expt 10 23)) 4 "orange")
   ;  (body "Havoc" (* -1.2 AU) 0 0 (* -10 1000) (* 8 (expt 10 25)) 50 "green")
   ))

(define (printBodies bodies scale) ;To print the numbers for control
  (if (equal? bodies '())
      (printf "Done\n")
      (let
          ([ p (printf "Position XY ~a \n" (list (body-id (car bodies))
                                                 (* (body-px (car bodies)) scale)
                                                 (* (body-py (car bodies)) scale)
                                                 (* (body-vx (car bodies)) scale)
                                                 (* (body-vy (car bodies)) scale)))])
        (printBodies (cdr bodies) scale))))

;; setup
(define Width 1200)
(define xoffset (/ Width 2))
(define Height 720)
(define yoffset (/ Height 2))

;; start-world (world left right ps vs as f)
(define starting-state testCollPlanets);position velocity
                             
;; world -> scene
(define (render-expr bodies)
  ;(printBodies bodies SCALE)
  (place-images
   (map (λ (b) (circle (body-radius b) "solid" (body-color b))) bodies)
   (map (λ (b) (make-posn (+ (* (body-px b) SCALE) xoffset )
                          (+ (* (body-py b) SCALE) yoffset ))) bodies)
   (empty-scene Width Height "black")))

;; world -> world
;; update velocities and positions
(define (tick-expr bodies)
  (gravity bodies timestep))

;;
(big-bang starting-state
  (on-tick tick-expr)          
  (to-draw render-expr Width Height))
```