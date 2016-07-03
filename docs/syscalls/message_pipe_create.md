# _magenta_message_pipe_create

## NAME

message_pipe_create - create a message pipe

## SYNOPSIS

```
#include <magenta/syscalls.h>

mx_handle_t _magenta_message_pipe_create(mx_handle_t* other_handle);

```

## DESCRIPTION

**message_pipe_create**() creates a message pipe, a bi-directional
datagram-style message transport capable of sending raw data bytes
as well as handles from one side to the other.

Two handles are returned on success, providing access to both sides
of the message pipe.  Messages written to one handle may be read
from the opposite.

The handles will have MX_RIGHT_TRANSFER (allowing them to be sent
to another process via message pipe write), MX_RIGHT_WRITE (allowing
messages to be written to them), and MX_RIGHT_READ (allowing messages
to be read from them).

## RETURN VALUE

**message_pipe_create**() returns a valid message pipe handle (positive)
on success, in which case the handle to the other side of the message
pipe is returned via the *other_handle* pointer.  In the event of failure,
a negative error value is returned.  Zero (the "invalid handle") is never
returned.

## ERRORS

**ERR_INVALID_ARGS**  *other_handle* is an inavlid pointer or NULL.

**ERR_NO_MEMORY**  (Temporary) Failure due to lack of memory.

## SEE ALSO

[handle_close](handle_close.md),
[handle_duplicate](handle_duplicate.md),
[handle_wait_one](handle_wait_one),
[handle_wait_many](handle_wait_many.md),
[message_read](message_read.md),
[message_write](message_write.md).
