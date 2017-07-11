# NAME

UV - Perl interface to libuv

# SYNOPSIS

    #!/usr/bin/env perl
    use strict;
    use warnings;

    use UV;

    # hi-resolution time
    my $hi_res_time = UV::hrtime();

    # A new loop
    my $loop = UV::Loop->new();

    # default loop
    my $loop = UV::Loop->default_loop(); # convenience constructor
    my $loop = UV::Loop->new(1); # Tell the constructor you want the default loop

    # run a loop with one of three options:
    # UV_RUN_DEFAULT, UV_RUN_ONCE, UV_RUN_NOWAIT
    $loop->run(); # runs with UV_RUN_DEFAULT
    $loop->run(UV::Loop::UV_RUN_DEFAULT); # explicitly state UV_RUN_DEFAULT
    $loop->run(UV::Loop::UV_RUN_ONCE);
    $loop->run(UV::Loop::UV_RUN_NOWAIT);

# DESCRIPTION

This module provides an interface to [libuv](http://libuv.org). We will try to
document things here as best as we can, but we also suggest you look at the
[libuv docs](http://docs.libuv.org) directly for more details on how things
work.

Event loops that work properly on all platforms. YAY!

# CONSTANTS

## ERROR CONSTANTS

### UV\_E2BIG

Argument list too long

### UV\_EACCES

Permission denied

### UV\_EADDRINUSE

Address already in use

### UV\_EADDRNOTAVAIL

Address not available

### UV\_EAFNOSUPPORT

Address family not supported

### UV\_EAGAIN

Resource temporarily unavailable

### UV\_EAI\_ADDRFAMILY

Address family not supported

### UV\_EAI\_AGAIN

Temporary failure

### UV\_EAI\_BADFLAGS

Bad ai\_flags value

### UV\_EAI\_BADHINTS

Invalid value for hints

### UV\_EAI\_CANCELED

Request canceled

### UV\_EAI\_FAIL

Permanent failure

### UV\_EAI\_FAMILY

ai\_family not supported

### UV\_EAI\_MEMORY

Out of memory

### UV\_EAI\_NODATA

No address

### UV\_EAI\_NONAME

Unknown node or service

### UV\_EAI\_OVERFLOW

Argument buffer overflow

### UV\_EAI\_PROTOCOL

Resolved protocol is unknown

### UV\_EAI\_SERVICE

Service not available for socket type

### UV\_EAI\_SOCKTYPE

Socket type not supported

### UV\_EALREADY

Connection already in progress

### UV\_EBADF

Bad file descriptor

### UV\_EBUSY

Resource busy or locked

### UV\_ECANCELED

Operation canceled

### UV\_ECHARSET

Invalid Unicode character

### UV\_ECONNABORTED

Software caused connection abort

### UV\_ECONNREFUSED

Connection refused

### UV\_ECONNRESET

Connection reset by peer

### UV\_EDESTADDRREQ

Destination address required

### UV\_EEXIST

File already exists

### UV\_EFAULT

Bad address in system call argument

### UV\_EFBIG

File too large

### UV\_EHOSTUNREACH

Host is unreachable

### UV\_EINTR

Interrupted system call

### UV\_EINVAL

Invalid argument

### UV\_EIO

i/o error

### UV\_EISCONN

Socket is already connected

### UV\_EISDIR

Illegal operation on a directory

### UV\_ELOOP

Too many symbolic links encountered

### UV\_EMFILE

Too many open files

### UV\_EMLINK

Too many links

### UV\_EMSGSIZE

Message too long

### UV\_ENAMETOOLONG

Name too long

### UV\_ENETDOWN

Network is down

### UV\_ENETUNREACH

Network is unreachable

### UV\_ENFILE

File table overflow

### UV\_ENOBUFS

No buffer space available

### UV\_ENODEV

No such device

### UV\_ENOENT

No such file or directory

### UV\_ENOMEM

Not enough memory

### UV\_ENONET

Machine is not on the network

### UV\_ENOPROTOOPT

Protocol not available

### UV\_ENOSPC

No space left on device

### UV\_ENOSYS

Function not implemented

### UV\_ENOTCONN

Socket is not connected

### UV\_ENOTDIR

Not a directory

### UV\_ENOTEMPTY

Directory not empty

### UV\_ENOTSOCK

Socket operation on non-socket

### UV\_ENOTSUP

Operation not supported on socket

### UV\_ENXIO

No such device or address

### UV\_EOF

End of file

### UV\_EPERM

Operation not permitted

### UV\_EPIPE

Broken pipe

### UV\_EPROTO

Protocol error

### UV\_EPROTONOSUPPORT

Protocol not supported

### UV\_EPROTOTYPE

Protocol wrong type for socket

### UV\_ERANGE

Result too large

### UV\_EROFS

Read-only file system

### UV\_ESHUTDOWN

Cannot send after transport endpoint shutdown

### UV\_ESPIPE

Invalid seek

### UV\_ESRCH

No such process

### UV\_ETIMEDOUT

Connection timed out

### UV\_ETXTBSY

Text file is busy

### UV\_EXDEV

Cross-device link not permitted

### UV\_UNKNOWN

Unknown error

## REQUEST TYPE CONSTANTS

### UV\_CONNECT

### UV\_FS

### UV\_GETADDRINFO

### UV\_GETNAMEINFO

### UV\_REQ

### UV\_SHUTDOWN

### UV\_UDP\_SEND

### UV\_WORK

### UV\_WRITE

## HANDLE TYPE CONSTANTS

### UV\_ASYNC

### UV\_CHECK

### UV\_FILE

### UV\_FS\_EVENT

### UV\_FS\_POLL

### UV\_HANDLE

### UV\_IDLE

### UV\_NAMED\_PIPE

### UV\_POLL

### UV\_PREPARE

### UV\_PROCESS

### UV\_SIGNAL

### UV\_STREAM

### UV\_TCP

### UV\_TIMER

### UV\_TTY

### UV\_UDP

# FUNCTIONS

The following functions are available:

## default\_loop

    my $loop = UV::default_loop();
    # You can also get it with the UV::Loop methods below:
    my $loop = UV::Loop->default_loop();
    my $loop = UV::Loop->default();
    # Passing a true value as the first arg to the UV::Loop constructor
    # will also return the default loop
    my $loop = UV::Loop->new(1);

Returns the default loop (which is a singleton object). This module already
creates the default loop and you get access to it with this method.

## hrtime

    my $uint64_t = UV::hrtime();

Get the current Hi-Res time (`uint64_t`).

# AUTHOR

Daisuke Murase <`typester@cpan.org`>

# CONTRIBUTORS

Chase Whitener <`capoeirab@cpan.org`>

# COPYRIGHT AND LICENSE

Copyright 2012, Daisuke Murase.

This library is free software; you can redistribute it and/or modify it under
the same terms as Perl itself.
