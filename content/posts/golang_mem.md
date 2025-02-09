---
title: "✧ Memory Layouts in Golang"
date: "2025-02-08T21:05:11-03:00"
tags: ["golang","flashcard",]
# title_images: [ "/mem.jpg"]
author: "fatima"
draft: false
---
<!-- introduction -->
Type Alignment and Memory Layout in Golang but simple :D
<!--more-->
<!-- rest of the content -->
- Type alignment is Golang is all about how data is arranged to ensure efficient access by the CPU. The starting memory address of a value of a certain type must be a multiple of an integer N. That sounds confusing but what this means is if a value takes up 2 bytes (int16) then the starting memory address should be even, e.g., 100, 102, etc. 

[ "/mem.jpg"]