Hello everyone!

A quick mail about "Systems and networks programming in Rust” lecture, read it entirely, there is some homework for you at the end. You will find a French version of this mail bellow ;)


# Recap from the previous sessions

## Rust basics (Introduction, Syntax, Error Handling):

- 0. Schedule, purpose, and rules of the class (planning, assignments, grades, etc..)

- 1. What's systems programming? Why systems (and networks) programming? Why Rust?

- 2. Setup a Rust dev environment with <https://rustup.rs>, and a code editor (<https://www.rust-lang.org/tools>) with RLS support (<https://github.com/rust-lang/rls>) and be sure to not have just the VSCode extension but to install it with command `rustup component add rls rust-analysis rust-src`

N.B. People on Windows should read this <https://github.com/rust-lang/rustup.rs/#working-with-rust-on-windows>, and installing Visual Studio C/C++ tools suite (like link.exe to link program) using Visual Studio Installer.

I also recommend to get you a WLS and install Rust with rustup in bash.exe, since starting from course 3 we will play with Linux file abstraction.

- 3. Get familiar with language syntax by playing a bit with <https://github.com/rust-lang/rustlings>

- 4. Theoretical recap about the semantics of a Rust program (we talk about functions VS macros, type inference, enumeration types <https://doc.rust-lang.org/std/result/enum.Result.html>)

- 5. Show off basic tooling: how to create a binary/library with cargo, how to add a dependency form crate.io to our project, we start writing a little MASTERMIND game (Here is a link to the full implementation <https://github.com/yvan-sraka/mymastermind>)

Further information could be found in THE RUST BOOK —> <https://doc.rust-lang.org/stable/book/> <— (what we do in class match the 3 first chapters of the book)

## Rust advanced (static automated memory management: Ownership & Borrowing)

- QCM is a huge success, the mean of the class is 13,67 / 20 (negative points are on me this time)

- I strongly advise you to try to finish rustlings to be more comfortable with basic language features <https://github.com/rust-lang/rustlings>

- The small Rust code I wrote in class to play with ownership and borrowing: <https://gist.github.com/yvan-sraka/81f3f6ea6e7147b69a334b023d71f0bb>

REMINDER: Rule of thumbs of Rust -> they cannot have both aliasing AND mutability!


# Program of the next lectures

- December 20: Files (standard IO, synchronous message through pipes), Tasks (process, thread) and other POSIX stuff
- January  10: No class!
- January  24: FFI, unsafe world (let’s talk about “lifetimes”) and the C runtime
- 2nd Semester: ***** NETWORK (finally, something fun) *****


# Mandatory for the next session (December 20)

⚠️ Have a UNIX system with Rust installed inside:

For those that run a Windows machine, I highly recommend the installation of a WSL (Windows Subsystem for Linux) <https://docs.microsoft.com/en-us/windows/wsl/install-win10>

and the nice VSCode extension <https://code.visualstudio.com/remote-tutorials/wsl/run-in-wsl> that allows you to run `code` command remotely in bash.exe shell!

(and, of course, to have a working Rust dev environment with RLS setup <https://github.com/rust-lang/rls>)


# Go deeper into Rust

We, at this point cover, all of 6 first chapters, and most of 7, 8 and 9 of the Rust Book <https://doc.rust-lang.org/stable/book/>

We will not advance to much in Rust specific feature after this point (I will not make a class about trait e.g.), I let you free of learning more about it or not!

I give you here three handy tools that will help you with homework and graded project:
- <https://github.com/rust-lang/rust-clippy>
- <https://github.com/rust-lang/rustfmt>
- <https://github.com/mre/cargo-inspect> (play with it!)


# Go deeper into memory

Try to create a small C program that creates a memory leak (like a loop that malloc but never free) and open it in Valgrind, translates the program in Rust and redo the test.

Do you know that the program stack has a fixed space size in memory? What’s happen when you fill it all with function calls? -> a stack overflow!

You can look at this minimalist malloc implementation from mine, using mmap syscall (read its man) to allocate memory pages: <https://github.com/yvan-sraka/malloc>

Supplementary links to feed your curiosity (bonus, not mandatory):

- There no null pointers in Rust! Why? Watch “Null References: The Billion Dollar Mistake” from Tony Hoare <https://www.infoq.com/presentations/Null-References-The-Billion-Dollar-Mistake-Tony-Hoare/>
- Some more readings for the brave: “What Every Programmer Should Know About Memory” by Ulrich Drepper from Red Hat <https://people.freebsd.org/~lstewart/articles/cpumemory.pdf>


## Homework (mandatory) - deadline: push it before the class

Make a PR (Pull-Request) on this repository that fixes this code: <https://github.com/rust-esgi/base64decode/blob/master/src/main.rs>

It will be automatically validated by GitHub Actions (Continuous Integration),

You can test your code by trying to decrypt this secret message:

    TGEgcmFjbGV0dGUgKEJyYXRjaMOkcywgwqsgZnJvbWFnZSDCuyByw7R0aSwgZW4gc3Vpc3NlIGFsbGVtYW5kKSBlc3QgZCd1bmUgcGFydCB1biBmcm9tYWdlIChsZSBvdSBsYSByYWNsZXR0ZSkgb3JpZ2luYWlyZSBkdSBjYW50b24gZHUgVmFsYWlzIGVuIFN1aXNzZSwgZXQgZCdhdXRyZSBwYXJ0LCB1bmUgcmVjZXR0ZSBkZSBjdWlzaW5lIHRyYWRpdGlvbm5lbGxlIGV0IGVtYmzDqW1hdGlxdWUgZGUgbGEgY3Vpc2luZSBzdWlzc2UsIGNvbm51ZSBkYW5zIGxlIG1vbmRlIGVudGllciwgdmFyaWFudGUgZGVzIGZvbmR1ZXMgYXUgZnJvbWFnZSwgw6AgYmFzZSBkZSBjZSBmcm9tYWdlIGZvbmR1LCByYWNsw6kgYXUgZnVyIGV0IMOgIG1lc3VyZSBxdeKAmWlsIGZvbmQsIGV0IHNlcnZpZSB0cmFkaXRpb25uZWxsZW1lbnQgYXZlYyBkZXMgcG9tbWVzIGRlIHRlcnJlIGVuIHJvYmUgZGVzIGNoYW1wcyBldCBhY2NvbXBhZ27DqWUgZGUgbMOpZ3VtZXMgYXUgdmluYWlncmUgKGNvcm5pY2hvbnMsIG9pZ25vbnMpLg==


# Big Project

I will present during the next class the final project on which you will be evaluated. You’re free to come with your idea of an alternative project if you have already in mind something that you want to code in Rust. I will accept any idea that could be reasonably doable by a group of 3 or 4 students (chosen randomly), that implies features specific to systems or networks programming (think about playing with binary encoding, intense computing with concurrent programming, low-level binding with another library or just any funny syscalls, etc…)!


Cheers, Yvan