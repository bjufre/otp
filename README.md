# Gleam OTP

<!-- <a href="https://github.com/gleam-lang/otp/releases"><img src="https://img.shields.io/github/release/gleam-lang/otp" alt="GitHub release"></a> -->
<a href="https://webchat.freenode.net/#gleam-lang"><img src="https://img.shields.io/badge/freenode%20chat-%23gleam--lang-blue" alt="IRC: #gleam-lang on chat.freenode.net"></a>
![CI](https://github.com/gleam-lang/otp/workflows/test/badge.svg?branch=master)

A Gleam library for building fault tolerant multi-core programs using the
actor model. It is compatible with Erlang's OTP framework.

This library is experimental and will likely have many breaking changes in the
future!


## Actor hierarchy

This library defines several different types of actor that can be used in
Gleam programs.

```
      Process
      ↙    ↘
   Actor   Task
     ↓
Supervisor
```

### Process

The process is the lowest level building block of OTP, all other actors are
built on top of processes either directly or indirectly. Typically this
abstraction would be not be used very often in Gleam applications, favour
other actor types that provide more functionality.

### Actor

The `actor` is the most commonly used actor type in Gleam and serves as a good
building block for other abstractions. Like Erlang's `gen_server` it will
automatically handle OTP's debug system messages for you.

### Task

A task is a kind of process that performs a single task and then shuts down.
Commonly tasks are used to convert sequential code into concurrent code by
performing computation in another process.

### Supervisor

Supervisors is a process that starts and then supervises a group of processes,
restarting them if they crash. Supervisors can start other supervisors,
resulting in a hierarchical process structure called a supervision tree,
providing fault tolerance to a Gleam application.
