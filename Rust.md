# cargo 命令
`cargo new project_name`
`cargo new file_name --name=project_name` // 文件名与项目名不同的项目
`cargo new lib_project --lib` // 创建一个带有库 crate 的项目

`cargo build` 编译，运行编译好的二进制文件（./target/debug/project_name）
`cargo run` 编译 + 运行，开发中常用
`cargo check` 编译但不打包，用于检查代码
`cargo build --release` 准备好发布时，打包编译（./target/release/project_name）

# 接收用户输入
```Rust
use std::io;

fn main() {
  let mut guess = String::new();
  io.stdin().read_line(&mut guess).expect("Failed to read line");
}
```

# 生成随机数
```Rust
use rand::Rng;

fn main() {
  let secret_number = rand::thread_rng().gen_range(1..=100);
}
```

# 打印输出
```Rust
#[derive(Debug)] // 添加属性以派生Debug特征
struct Rectangle {
  width: u32,
  height: u32,
}

fn main() {
  // 直接打印基本数据类型
  let a = 1;
  println!("{a}");

  // 打印复杂数据类型
  // 需要在数据类型前添加 #[derive(Debug)]，以添加派生属性
  let rect1 = Rectangle {
    width: 30,
    height: 50,
  };
  println!("rect1 is {rect1:?}"); // 使一行打印没有结构
  println!("rect1 is {rect1:#?}"); // 结构打印
  dbg!(&rect1); // debug 时打印
}
```