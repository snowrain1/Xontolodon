extern crate nix;
extern crate axon;

use std::env;
use std::process::Command;
use std::io::{Read,Write};

use axon::CommandExt;

fn main() {
    if env::args().len() > 1 {
        child();
        return;
    }
    let mut child = Command::new(env::current_exe().unwrap())
        .arg("child")
        .spawn_with_axon()
        .expect("Failed to start echo process");

    child.io.write("yolo".as_bytes()).unwrap();

    let mut b = vec![0;20];
    child.io.read(&mut b).unwrap();
    println!("recv in parent: {:?}", b);

    let ecode = child.c.as_mut().unwrap().wait().expect("failed to wait on child");
    assert!(ecode.success());
}

fn child() {
    let mut io = axon::child();
    let mut b = vec![0;10];
    io.read(&mut b).expect("reading from axiom file descriptor");
    println!("recv in child: {:?}", b);
    io.write("ok got it".as_bytes()).expect("sending on axiom failed");
    println!("child is bye bye");
}
