Hello everyone!

A quick mail about "Systems and networks programming in Rust” lecture, read it entirely, there is some homework for you at the end. You will find a French version of this mail bellow ;)


# Recap from the previous sessions

## Rust basics (Introduction, Syntax, Error Handling):

- 0. Schedule, purpose, and rules of the class (planning, assignments, grades, etc..)

- 1. What's systems programming? Why systems (and networks) programming? Why Rust?

- 2. Setup a Rust dev environment with https://rustup.rs, and a code editor (https://www.rust-lang.org/tools) with RLS support (https://github.com/rust-lang/rls) and be sure to not have just the VSCode extension but to install it with command `rustup component add rls rust-analysis rust-src`

N.B. People on Windows should read this https://github.com/rust-lang/rustup.rs/#working-with-rust-on-windows, and installing Visual Studio C/C++ tools suite (like link.exe to link program) using Visual Studio Installer.

I also recommend to get you a WLS and install Rust with rustup in bash.exe, since starting from course 3 we will play with Linux file abstraction.

- 3. Get familiar with language syntax by playing a bit with https://github.com/rust-lang/rustlings

- 4. Theoretical recap about the semantics of a Rust program (we talk about functions VS macros, type inference, enumeration types https://doc.rust-lang.org/std/result/enum.Result.html)

- 5. Show off basic tooling: how to create a binary/library with cargo, how to add a dependency form crate.io to our project, we start writing a little MASTERMIND game (Here is a link to the full implementation https://github.com/yvan-sraka/mymastermind)

Further information could be found in THE RUST BOOK —> https://doc.rust-lang.org/stable/book/ <— (what we do in class match the 3 first chapters of the book)

## Rust advanced (static automated memory management: Ownership & Borrowing)

- QCM is a huge success, the mean of the class is 13,67 / 20 (negative points are on me this time)

- I strongly advise you to try to finish rustlings to be more comfortable with basic language features https://github.com/rust-lang/rustlings

- The small Rust code I wrote in class to play with ownership and borrowing: https://gist.github.com/yvan-sraka/81f3f6ea6e7147b69a334b023d71f0bb

REMINDER: Rule of thumbs of Rust -> they cannot have both aliasing AND mutability!


# Program of the next lectures

- December 20: Files (standard IO, synchronous message through pipes), Tasks (process, thread) and other POSIX stuff
- January  10: No class!
- January  24: FFI, unsafe world (let’s talk about “lifetimes”) and the C runtime
- 2nd Semester: ***** NETWORK (finally, something fun) *****


# Mandatory for the next session (December 20)

/!\ Have a UNIX system with Rust installed inside:

For those that run a Windows machine, I highly recommend the installation of a WSL (Windows Subsystem for Linux) https://docs.microsoft.com/en-us/windows/wsl/install-win10

and the nice VSCode extension https://code.visualstudio.com/remote-tutorials/wsl/run-in-wsl that allows you to run `code` command remotely in bash.exe shell!

(and, of course, to have a working Rust dev environment with RLS setup https://github.com/rust-lang/rls)


# Go deeper into Rust

We, at this point cover, all of 6 first chapters, and most of 7, 8 and 9 of the Rust Book https://doc.rust-lang.org/stable/book/

We will not advance to much in Rust specific feature after this point (I will not make a class about trait e.g.), I let you free of learning more about it or not!

I give you here three handy tools that will help you with homework and graded project:
- https://github.com/rust-lang/rust-clippy
- https://github.com/rust-lang/rustfmt
- https://github.com/mre/cargo-inspect (play with it!)


# Go deeper into memory

Try to create a small C program that creates a memory leak (like a loop that malloc but never free) and open it in Valgrind, translates the program in Rust and redo the test.

Do you know that the program stack has a fixed space size in memory? What’s happen when you fill it all with function calls? -> a stack overflow!

You can look at this minimalist malloc implementation from mine, using mmap syscall (read its man) to allocate memory pages: https://github.com/yvan-sraka/malloc

Supplementary links to feed your curiosity (bonus, not mandatory):

- There no null pointers in Rust! Why? Watch “Null References: The Billion Dollar Mistake” from Tony Hoare https://www.infoq.com/presentations/Null-References-The-Billion-Dollar-Mistake-Tony-Hoare/
- Some more readings for the brave: “What Every Programmer Should Know About Memory” by Ulrich Drepper from Red Hat https://people.freebsd.org/~lstewart/articles/cpumemory.pdf


## Homework (mandatory) - deadline: push it before the class

Make a PR (Pull-Request) on this repository that fixes this code: https://github.com/rust-esgi/base64decode/blob/master/src/main.rs

It will be automatically validated by GitHub Actions (Continuous Integration),

You can test your code by trying to decrypt this secret message:

TGEgcmFjbGV0dGUgKEJyYXRjaMOkcywgwqsgZnJvbWFnZSDCuyByw7R0aSwgZW4gc3Vpc3NlIGFsbGVtYW5kKSBlc3QgZCd1bmUgcGFydCB1biBmcm9tYWdlIChsZSBvdSBsYSByYWNsZXR0ZSkgb3JpZ2luYWlyZSBkdSBjYW50b24gZHUgVmFsYWlzIGVuIFN1aXNzZSwgZXQgZCdhdXRyZSBwYXJ0LCB1bmUgcmVjZXR0ZSBkZSBjdWlzaW5lIHRyYWRpdGlvbm5lbGxlIGV0IGVtYmzDqW1hdGlxdWUgZGUgbGEgY3Vpc2luZSBzdWlzc2UsIGNvbm51ZSBkYW5zIGxlIG1vbmRlIGVudGllciwgdmFyaWFudGUgZGVzIGZvbmR1ZXMgYXUgZnJvbWFnZSwgw6AgYmFzZSBkZSBjZSBmcm9tYWdlIGZvbmR1LCByYWNsw6kgYXUgZnVyIGV0IMOgIG1lc3VyZSBxdeKAmWlsIGZvbmQsIGV0IHNlcnZpZSB0cmFkaXRpb25uZWxsZW1lbnQgYXZlYyBkZXMgcG9tbWVzIGRlIHRlcnJlIGVuIHJvYmUgZGVzIGNoYW1wcyBldCBhY2NvbXBhZ27DqWUgZGUgbMOpZ3VtZXMgYXUgdmluYWlncmUgKGNvcm5pY2hvbnMsIG9pZ25vbnMpLg==


# Big Project

I will present during the next class the final project on which you will be evaluated. You’re free to come with your idea of an alternative project if you have already in mind something that you want to code in Rust. I will accept any idea that could be reasonably doable by a group of 3 or 4 students (chosen randomly), that implies features specific to systems or networks programming (think about playing with binary encoding, intense computing with concurrent programming, low-level binding with another library or just any funny syscalls, etc…)!


Cheers, Yvan

---

Bonjour à tous!

L’anglais ce n’est pas votre truc, je ne vous en veux pas :)


# Récapitulatif des sessions précédentes

## Notions de base sur Rust (Introduction, Syntaxe, Traitement des erreurs):

- 0. Horaires, but et règles de la classe (planning, devoirs maisons, notes, etc.)

- 1. Qu'est-ce que la programmation système ? Pourquoi programmer des systèmes (et des réseaux) ? Pourquoi Rust ?

- 2. Configurez un environnement de développement Rust avec https://rustup.rs et un IDE (https://www.rust-lang.org/tools) avec support RLS (https://github.com/rust- lang / rls) vous avez besoin de l'extension VSCode, mais de lancer cette commande `rustup component add rls rust-analysis rust-src`

N.B. Les utilisateurs de Windows doivent lire ce guide https://github.com/rust-lang/rustup.rs/#working-with-rust-on-windows et installer la suite d'outils Visual Studio C / C++ (contenant par exemple link.exe) à l’aide de Visual Studio Installer.

Je vous recommande également de vous procurer un WLS et d’installer Rust avec rustup dans bash.exe, puisqu’à partir du cours 3, nous allons jouer avec l’abstraction de fichiers Linux.

- 3. Familiarisez-vous avec la syntaxe du langage en jouant un peu avec https://github.com/rust-lang/rustlings

- 4. Récapitulation théorique de la sémantique d'un programme Rust (on a parlé de fonctions VS macros, d’inférence de types, d'énumérations https://doc.rust-lang.org/std/result/enum.Result.html)

- 5. Les outils de base : comment créer une bibliothèque / binaire avec cargo, comment ajouter une dépendance crate.io à notre projet, nous avons commencé à écrire un petit jeu MASTERMIND (voici un lien vers l’implémentation complète https://github.com/yvan-sraka/mymastermind)

Des informations complémentaires sont disponibles dans THE RUST BOOK -> https://doc.rust-lang.org/stable/book/<- (ce que nous avons fait en classe correspond aux 3 premiers chapitres du livre)

## Rust avancé (gestion automatique de la mémoire statique: « ownership » et « borrowing »)

- Le QCM est un énorme succès, la moyenne de la classe est de 13,67 / 20 (les points négatifs sont pour moi cette fois)

- Je vous conseille vivement d'essayer de finir les exercices « rustlings » pour être plus à l'aise avec les fonctionnalités de base du langage https://github.com/rust-lang/rustlings

- Le petit code Rust que j'ai écrit en classe pour jouer avec les concepts d’« ownership » et de « borrowing » : https://gist.github.com/yvan-sraka/81f3f6ea6e7147b69a334b023d71f0bb

RAPPEL: règle d’or de Rust -> il ne peut pas avoir à la fois de l’aliasing ET de la mutabilité!


# Programme des prochaines séances

- 19 décembre: fichiers (E / S standard, message synchrone via des pipes), tâches (processus, thread) et autres POSIXeries
- 10 janvier : Pas de cours !
- 24 janvier : FFI,  unsafe mode (parlons de « lifetimes ») et binaires

- 2nd Semestre : ***** NETWORK (enfin, quelque chose d'amusant) *****


# Obligatoire pour la prochaine session (20 Décembre)

/!\ Avoir un système UNIX avec Rust installé dessus :

Pour ceux qui exécutent une machine Windows, je recommande vivement l'installation d'un WSL (Sous-système Windows pour Linux) https://docs.microsoft.com/en-us/windows/wsl/install-win10

et de l’extension VSCode qui va bien https://code.visualstudio.com/remote-tutorials/wsl/run-in-wsl qui vous permet d'exécuter la commande `code` à distance dans un shell bash.exe!

(et, bien sûr, d’avoir un environnement de développement Rust fonctionnel avec RLS activé https://github.com/rust-lang/rls)


# Aller plus loin dans Rust

Nous avons couvert jusqu’à présent les 6 premiers chapitres et la plupart des 7, 8 et 9 du Rust Book https://doc.rust-lang.org/stable/book/

Nous n’avancerons pas beaucoup dans les fonctionnalités spécifiques de Rust à partir de maintenant (je ne ferai, par exemple, pas de cours sur les traits), je vous laisse libre d’en apprendre davantage sur le sujet ou pas!

Je vous donne ici trois outils pratiques qui vous aideront avec vos devoirs et votre projet noté:
- https://github.com/rust-lang/rust-clippy
- https://github.com/rust-lang/rustfmt
- https://github.com/mre/cargo-inspect (jouez avec !)


# Aller plus loin dans la mémoire

Essayez de créer un petit programme en C qui crée une fuite de mémoire (comme une boucle qui « malloc » mais qui ne « free » jamais) et ouvrez-le dans Valgrind, traduisez le programme en Rust et refaites le test.

Savez-vous que la pile d’un programme a une taille fixe dans l’espace mémoire ? Que se passe-t-il lorsque vous dépassez l’espace disponible avec trop d’appels de fonction ? -> « stack overflow » !

Vous pouvez regarder cette implémentation malloc minimaliste, basé sur l’appel système mmap (lisez son manuel) pour allouer des pages de mémoire : https://github.com/yvan-sraka/malloc

Quelques liens supplémentaires pour nourrir votre curiosité (en bonus, non obligatoire):

- Il n'y a pas de pointeurs « null » dans Rust! Pourquoi? Regardez “Null References: The Billion Dollar Mistake” de Tony Hoare https://www.infoq.com/presentations/Null-References-The-Billion-Dollar-Mistake-Tony-Hoare/
- Quelques lectures supplémentaires pour les plus courageux: “What Every Programmer Should Know About Memory” de Ulrich Drepper chez Red Hat https://people.freebsd.org/~lstewart/articles/cpumemory.pdf


# Devoir maison (obligatoire) - date limite: à envoyer avant le cours

Créez une PR (Pull-Request) sur ce repos qui corrige les bugs de ce code: https://github.com/rust-esgi/base64decode

Il sera automatiquement validé par GitHub Actions (Intégration Continue), donc si c’est vert, vous avez déjà une bonne note. Je vous donnerai des points supplémentaires si vous parvenez à réduire la taille du code sans le casser!

Vous pouvez tester votre code en essayant de déchiffrer ce message secret:

TGEgcmFjbGV0dGUgKEJyYXRjaMOkcywgwqsgZnJvbWFnZSDCuyByw7R0aSwgZW4gc3Vpc3NlIGFsbGVtYW5kKSBlc3QgZCd1bmUgcGFydCB1biBmcm9tYWdlIChsZSBvdSBsYSByYWNsZXR0ZSkgb3JpZ2luYWlyZSBkdSBjYW50b24gZHUgVmFsYWlzIGVuIFN1aXNzZSwgZXQgZCdhdXRyZSBwYXJ0LCB1bmUgcmVjZXR0ZSBkZSBjdWlzaW5lIHRyYWRpdGlvbm5lbGxlIGV0IGVtYmzDqW1hdGlxdWUgZGUgbGEgY3Vpc2luZSBzdWlzc2UsIGNvbm51ZSBkYW5zIGxlIG1vbmRlIGVudGllciwgdmFyaWFudGUgZGVzIGZvbmR1ZXMgYXUgZnJvbWFnZSwgw6AgYmFzZSBkZSBjZSBmcm9tYWdlIGZvbmR1LCByYWNsw6kgYXUgZnVyIGV0IMOgIG1lc3VyZSBxdeKAmWlsIGZvbmQsIGV0IHNlcnZpZSB0cmFkaXRpb25uZWxsZW1lbnQgYXZlYyBkZXMgcG9tbWVzIGRlIHRlcnJlIGVuIHJvYmUgZGVzIGNoYW1wcyBldCBhY2NvbXBhZ27DqWUgZGUgbMOpZ3VtZXMgYXUgdmluYWlncmUgKGNvcm5pY2hvbnMsIG9pZ25vbnMpLg ==


# Projet final

Lors du prochain cours, je présenterai le projet final sur lequel vous serez évalué. Vous êtes libre de proposer des idées de projets alternatifs si vous avez déjà en tête quelque chose que vous souhaitez coder dans Rust. J'accepterai toute idée raisonnablement réalisable par un groupe de 3 ou 4 étudiants (choisis au hasard), qui implique des fonctionnalités spécifiques à la programmation système ou réseau (pensez à jouer avec un encodage binaire, des programmes concurrents qui font des calculs, de l’interopérabilité bas niveau avec une autre bibliothèque ou des appels systèmes, etc ...)!

Amitiés, Yvan