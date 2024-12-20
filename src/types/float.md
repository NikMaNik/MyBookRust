## Float

В `Rust` есть два примитивных типа для чисел с плавающей точкой.
1. f32 (32 бита)
2. f64 (64 бита) 
 
Тип по умолчанию `f64`, т.к. в современных процессорах он работает примерно с той же 
скоростью, что и `f32` но обладает большей точностью.

| Формат | Диапазон                                             |
|--------|------------------------------------------------------|
| `f32`  | от \\( -3.4 * 10^{38} \\) до \\( 3.4 * 10^{38}  \\)  | 
| `f64`  | от \\( -1.8 * 10^{308} \\) до \\( 1.8 * 10^{308} \\) | 

`Rust` использует округление до ближайшего четного, что является режимом округления в IEEE 754;

```rust
#fn main() {
    let number:f32 = 3.141592653589;
    println!("32 бита: {}", number);
    let number:f64 = 3.141592653589;
    println!("64 бита: {}", number);
    let number = 3.141592_f32; // поддерживает суффикс типа 
    println!("суффикс типа 32 бита: {}", number);
    let number = 3.141592653589_f64; // f64
    println!("суффикс типа 64 бита: {}", number);
    let number:f64 = 3.141592653589;
    println!("ограничение, 3 знака после запятой {:.3}", number);
    let number:f64 = 3.141592653589;
    let prec:usize = 4; // использование переменной в ограничение после запятой
    println!("ограничение, {} знака после запятой: {:.prec$}", prec, number)
#}
```
