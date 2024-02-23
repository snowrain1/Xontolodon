extern crate axon;

use std::io::{Read,Write};

fn main() {
    let mut io = axon::child();
    let mut b = vec![0;10];
    io.write("ok got it".as_bytes()).expect("sending on axiom failed");
    io.write("yooo lol".as_bytes()).expect("sending on axiom failed");
}
