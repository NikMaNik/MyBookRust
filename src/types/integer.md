### Целочисленный тип данных

Целочисленный тип ***(Integer)*** - это числа без дробной части.

| Длина                  | Со знаком | Без знака | 
|------------------------|-----------|-----------|
| 8 бит                  | i8        | u8        |
| 16 бит                 | i16       | u16       |
| 32 бита                | i32       | u32       |
| 64 бита                | i64       | u64       |
| 128 бита               | i128      | u128      |
| архитектурно-зависимая | isize     | usize     |

В **Rust** - есть два вида целочисленного типа.  
`Isize` - позволяет хранить числа со знаком N: -100;  
Может хранить значения от \\(-(2^{n-1})\\) до \\((2^{n-1})-1\\)
* Интерактивный компилятор можно поменять bytes
```rust,editable
fn main() {
    let bytes = 8;
    let x: i128 = -(2_i128.pow(bytes - 1)); 
    let y: i128 = 2_i128.pow(bytes - 1) - 1; 
    println!("от {} до {}", x, y);
}
```


`Usize` - позволяет хранить только положительные числа N: 100;  
Может хранить числа от **0** до \\(2^n - 1\\)
* Интерактивный компилятор можно поменять bytes
```rust,editable
fn main(){
    let bytes = 8;
    let x: u128 = (2_u128.pow(bytes)-1);
    println!("от 0 до {}", x);
}
```
Кроме того, типы `usize` и `isize` зависят от архитектуры компьютера, на котором
выполняется программа, и обозначается как `arch`:64 бита если используется
64 битная архитектура, и 32 бита если используется 32-битная архитектура.  
`isize` и `usize`- используются, как правило, для обозначения индекса коллекций.

Существует способ записи чисел нужного типа так, что бы компилятор автоматически определял
тип без аннотации типа, а именно механизм ***вывода / инференции типа (type inference)***.  
***Type Inference***- процесс, при котором компилятор `Rust` самостоятельно определяет тип
переменной на основе получаемого значения и как переменная используется впоследствии.  
Для ***Type Inference*** используются числовые литералы с суффиксами типа, которые описывают себя.
Так же числовые литералы можно записывать с использованием `_` (пример будет показан ниже).
```rust
# fn main() {
    let age = 25u8;  // в этом примере компилятор определит число 20 как тип `u8`
    println!("компилятор определит число 20 как тип `u8`: {}", age);   
    
    let number = 1_000_000; // пример записи числового литерала с использованием _
    println!("запись числового литерала с использованием _ :{}", number);
    
    let number: i64 = 1_000_000; //  используем анотацию типа после переменной
    println!("анотация типа после переменной: {}", number);
    
    let number = 1_000_000i32; // используем анотацию типа в конце числа
    println!("анотация типа в конце числа: {}", number);
    
    let number = 1_000_000_i32; //используем анотацию типа в конце числа с _
    println!("анотация типа в конце числа с `_` :{}", number)
#}
```
Если мы не объявляем аннотацию типа `Rust` по умолчанию назначает тип i32.
```rust
#use std::any::type_name;
#fn main() {
    let x = 1_000_000;
    println!("Тип переменной x: {}", type_of(&x));
#}
#fn type_of<T>(_: &T) -> &'static str {
#    type_name::<T>()
#}
```  

## Формат записи целых чисел

`Rust` позволяет записывать целочисленные типы разными форматами счисления.

| Формат Записи                                 |        Литерал         | Спецификатор формата |
|-----------------------------------------------|:----------------------:|:--------------------:|
| Десятичная                                    |       1_000_000        |                      |
| Шестнадцатеричная                             |         F4240          |    `:X` или `:#X`    |
| Восьмеричная                                  |       0o3641100        |    `:o` или `:#o`    |
| Двоичная                                      | 0b11110100001001000000 |    `:b` или `:#b`    |
| Байтовая - одиночный символ ASCII (только u8) |         `b'A'`         |          -           |

```rust
#fn main(){
    let number = 1_000_000;

    println!("Шестнадцатиричная система счсисления: {number:X} или {number:#X}");
    println!("Восьмиричная система счисления: {:#o}", number);
    println!("Двоичная система счисления: {:#b}", number);
#}
```