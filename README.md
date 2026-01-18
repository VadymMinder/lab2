<p align="center"><b>МОНУ НТУУ КПІ ім. Ігоря Сікорського ФПМ СПіСКС</b></p>
<p align="center">
<b>Звіт з лабораторної роботи 2</b><br/>
"Рекурсія"<br/>
дисципліни "Вступ до функціонального програмування"
</p>
<p align="right"><b>Студент(-ка)</b>: Міндер Вадим Юрійович КВ-22</p>
<p align="right"><b>Рік</b>: 2026</p>

## Загальне завдання
<!-- Зазначається загальне завдання -->
## Варіант <16>
<!-- Зазначається завдання за варіантом -->
## Лістинг функції < reverse-and-nest-head >
```lisp
(defun reverse-and-nest-head (lst)
  "Reverse list and build nested structure starting from head"
  (cond
    ((null lst) nil)

    ((null (cdr lst))
     (list (list (car lst))))

    ((null (cddr lst))
     (list (list (car (reverse-and-nest-head (cdr lst)))
                 (car lst))))

    (t
     (list (car (reverse-and-nest-head (cdr lst)))
           (car lst)))))
```

### Тестові набори та утиліти
```lisp
(defun check-reverse-and-nest-head (name input expected)
    "Execute `my-reverse' on `input', compare result with `expected' and print
    comparison status"
    (format t "~:[FAILED~;passed~] ~a~%"
        (equal (reverse-and-nest-head input) expected)
        name))

(defun test-reverse-and-nest-head ()
  (check-reverse-and-nest-head
   "test 1" '(a b c) '(((c) b) a))
  (check-reverse-and-nest-head
   "test 2" '(1 2) '(((2) 1)))
  (check-reverse-and-nest-head
   "test 3" '(x) '((x)))
  (check-reverse-and-nest-head
   "test 4" nil nil))
```

### Тестування

```lisp
* (test-reverse-and-nest-head)
passed test 1
passed test 2
passed test 3
passed test 4
NIL
```
## Лістинг функції < duplicate-elements >
```lisp
(defun duplicate-element (el n)
  "Duplicate element el n times"
  (if (<= n 0)
      nil
      (cons el (duplicate-element el (1- n)))))

(defun duplicate-elements (lst n)
  "Duplicate each element of lst n times"
  (if (null lst)
      nil
      (append (duplicate-element (car lst) n)
              (duplicate-elements (cdr lst) n))))
```
### Тестові набори та утиліти
```lisp
(defun check-duplicate-elements (name input n expected)
  "Execute `duplicate-elements' on `input', compare result with `expected' and print
	comparison status"
  (format t "~:[FAILED~;passed~]... ~a~%"
          (equal (duplicate-elements input n) expected)
          name))

(defun test-duplicate-elements ()
  (check-duplicate-elements
   "test 1" '(a b c) 3 '(a a a b b b c c c))
  (check-duplicate-elements
   "test 2" '(1 2) 2 '(1 1 2 2))
  (check-duplicate-elements
   "test 3" '(x) 5 '(x x x x x))
  (check-duplicate-elements
   "test 4" nil 3 nil))
```
### Тестування
```lisp
* (test-duplicate-elements)
passed... test 1
passed... test 2
passed... test 3
passed... test 4
NIL
*
```