---
title: "CEL is Funky"
date: "2025-02-09T21:05:11-03:00"
tags: ["CEL","PKI","OpenBao",]
author: "fatima"
draft: false
---

When I initially created this blog title, I was trying to return a single object from 
my CEL Program compiled with just 1 line of code (not really one line though lol).
I tediously (and naively) iterated through my struct, compiling each item 
and appending to another struct.

Geff, who was also working on a CEL PR, pointed me in the direction of protos in CEL.
I hadn't worked with protos before and so didn't know how they worked and wasn't confident
it would work out..? 💭_It would be pretty funky if i could compile the whole template in a line of code_ Turns out CEL is pretty funky ;)

### A 30-Second Proto Crash-Course  

* **What is it?** A language-neutral, binary-compact way to define structured data.  
* **Why care in CEL?** You get type safety, zero field-order anxiety and most of all minimal, clean code.

An example of a proto message that defines 2 certificate fields:

```proto
// pki_validation.proto
syntax = "proto3";

message CertTemplate {
  string common_name = 1;
  bool   is_valid    = 2;
  … imagine 35 more fields here 😱
}
```

The final CertTemplate had about 37 fields so you can just imagine how horrible it would've been iterating
through and processing each field individually.

Compiling this proto object would require registering it into the CEL environment (so CEL knows how it's 
defined) and simply compiling your request of type `CertTemplate`. ✨

### Overall thoughts on CEL

CEL is a super chill non-turing complete language. The syntax is pretty straightforward and there's not 
a lot of _magic_ 🪄 behind the scenes. Creating CEL programs is reminiscent of Logic and Proof. Golang 
has awesome CEL support and CEL itself was written in Golang.

If you’re hacking on CEL in OpenBao or anywhere, feel free to ping me on GitHub @[@fatima2003](https://github.com/fatima2003) :D
