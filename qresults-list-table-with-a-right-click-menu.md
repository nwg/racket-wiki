```racket
#lang racket
(require racket/gui/base
         qresults-list
         )

;Since qresults-list is an extension of list-box, you can send the same messages to it as you can send
;to a list-box%.  See the manual for list-box for these messages.

;You need to define functions which will return a given column value from a row of data.
; The variable data below is expected to be a vector.
;These functions typically have the name of the column.
;For database results you need to handle the fact that
;list-box can not display sql-null so you will need to
;substitute either "" or #f.  The sql-column-ref function
;from the dbutil.rkt file of ActivityLog2 does this.
(define (column1 data) (vector-ref data 0)) ;This function defines column1 as being the column at index 0.
(define (column2 data) (vector-ref data 1))

; The qcolumn struct defines a column of a qresults-list table.
; You provide qresults-list a list of these structs to define all the columns.
; The qcolumn constructor takes name, formatter and a sort-key.
; Name is a function which returns the correct value for a given column from a row of data.
;;Formatter is a function taking a row and returning a string representing
;;the value to be displayed for that row in this column.
;; You may want to enforce data types on input rather than use the formatter.
;;However, the formatter does have to handle any special cases.  For example, a numeric
;;column's formatter  should probably return empty string for null.
   ;; sort-key is function taking a row and returning a value that can be used to sort
   ;; this column, this can be either a string (in which case the column is
   ;; sorted by string< and string>, or a number in that case, the column is
   ;; sorted using < and >.
(define my-columns 
  (list
   (qcolumn "Column1" column1 column1)
   (qcolumn "Column2"
            (lambda (row)
              (if (number? (column2 row)) (number->string (column2 row)) "");This allows a cell to be blank.
              )
            column2)
   
   )
  )

;Create a frame to contain the table.
(define frame3 (new frame% 
                  [label "myTable 3"]
                  [width 800]
                  [height 600]
                  ))

(define (enable-disable-row-menu-items m) ;for actions on rows of the table.
;Some menus need to be greyed out when there is no selection.  Otherwise, you get an error
  ;when you right click and hit an action which needs a selection.
  ;Each menu item which acts on one or more rows of the table should appear here, in this function.
  (send info-menu-item enable (send table3 get-selected-row-index))
    (send delete-menu-item enable (send table3 get-selected-row-index))
  )

;Create the menu.  We add items to it next.
(define row-edit-menu (new popup-menu% 
                           (demand-callback enable-disable-row-menu-items))
  )

;Keyboard shortcuts defined in menu-items which only appear in a popup menu will only work when
;the popup menu is shown.  This is not an issue if you follow Apple's HIG because any item in
;a popup menu is also supposed to appear in the main menu bar.  Then the
;keyboard shortcuts will be available all the time.  

(define info-menu-item (new menu-item%
                              (label "info")
                              (parent row-edit-menu)
                              (shortcut #\i)
                              (callback (lambda (menu-item event)
                                          (message-box "Info"
                                                       (~a "You have selected " (length (send table3 get-selected-row-indexes)) " rows")
                                                       #f)
                                          ))
                              ))

(define delete-menu-item  (new menu-item%
                               (label "Delete Row(s)")
                               (parent row-edit-menu)
                               (shortcut #\backspace); command-delete on Mac, control-backspace on Linux and Windows.
                               (callback (lambda (menu-item event)
                                           (for ([row (reverse (send table3 get-selected-row-indexes))])
                                             ;Need to delete in reverse order because the rows renumber after each iteration of the loop.
                                             ;(displayln (~a "deleting row " row))
                                             (send table3 delete-row row))
                                           ))
                               ))

(define add-new-row (new menu-item%
                         (label "New row")
                         (parent row-edit-menu)
                         (shortcut #\n)
                         (callback (lambda (menu-item event)
                                     (send table3 add-row (vector "" ""))
                                     ))
                         ))

(define table3
       (new (class qresults-list% (init) (super-new)
              (define/override (on-double-click row-index row-data)
                ;on-double-click is defined in qresults-list but does nothing except return false.
                ;This override allows the double click to do somethig else.
                       (message-box "Info"
                                    (~a "You double clicked on row " row-index " which has data: " row-data)
                                    #f)
               
                ))
  [parent frame3]
  [pref-tag 'preferences-tag]
  [selection-type 'multiple]
  [right-click-menu row-edit-menu])
  )

(send table3 setup-column-defs my-columns)

(send frame3 show #t)

;The add-row message is part of qresults-list, not the parent list-box.
(send table3 add-row (vector "R1C1" 10))
(send table3 add-row (vector "R2C1" 11))
(send table3 add-row (vector "R3C1" 12))
;(send table3 add-row (vector "" "")) ;An empty row.
(send table3 add-row (vector "R4C1" 13))
(send table3 add-row (vector "R5C1" 14))
(send table3 add-row (vector "R5C1" 15))
(send table3 add-row (vector "R6C1" 16))
(send table3 add-row (vector "R7C1" 17))  

#| 
If you want to insert a blank row, you still need to fill it with null types.  For string types, you can use empty string.  
For numeric types, you can use +nan.0 but, unfortunately, the table will display this item explicity and not as a blank 
cell.
|#
