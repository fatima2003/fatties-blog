---
title: "✧ Memory Layouts in Golang"
date: "2025-02-08T21:05:11-03:00"
tags: ["golang","flashcard",]
title_images: [ "/mem.png"]
author: "fatima"
draft: false
---
<!-- introduction -->
Type Alignment and Memory Layout in Golang but simply :D
<!--more-->
<!-- rest of the content -->
### WHAT is Type alignment
- Type alignment is Golang is all about how data is arranged to ensure efficient access by the CPU. The starting memory address of a value of a certain type must be a multiple of an integer N, where N is the size of the type. That sounds confusing but what this means is if a value takes up 2 bytes (int16) then the starting memory address should be even, e.g., 100, 102, etc. 
- This N is called the alignment guarantee of the type.
### WHY Type Align
- Modern CPUs fetch data from memory in chunks. If data is not aligned properly, the CPU may need to read multiple memory locations instead of just one, causing performance issues.
- E.g., if a uint32 (4 bytes) starts at memory address 102, the CPU has to read extra bytes across boundaries (e.g., part from 102-103 and part from 104-105), which slows things down.

## Field vs. General Alignment

*General alignment*: When used as a standalone variable.
*Field alignment*: When used inside a struct.

- The alignment of a struct depends on the alignment of its fields. The largest alignment requirement among the fields determines the struct's alignment.
- For example:

type S struct {
    
    x int8    // 1-byte 

    y int64   // 8-byte 
}

* x as a standalone variable has an alignment of 1.
* But inside S, x is followed by y (which needs to be 8-byte aligned), so the compiler adds padding.

_Total size = 1 + 7 (padding) + 8 = 16 bytes_
