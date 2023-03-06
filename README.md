# Glisten

Simple python logging library - because I write this code in every project.

## Usage

```
import glisten

log = glisten.log.Logger('.log')

log.warn('A warning message')
```

produces:

`>>> A warning message`.

You can set `verbose` to False to suppress terminal messages (though it will always log to disk):

```
import glisten

log = glisten.log.Logger('.log', verbose=False)

log.warn('Terminal can\'t see this')```

will produce no terminal output, but `.log` will contain `[Warning] Terminal can't see this`.

Newlines get nicely formatted:

```
import glisten

log = glisten.log.Logger('.log')

log.warn("""This is a long message.
It spans multiple lines.
I like pizza.""")
```

produces:

```
[Warning] This is a long message.
           |     It spans multiple lines.
           |     I like pizza.
```

## Log types

- warn
- error
- deprecation

## Deprecations

`glisten` also provides a deprecation wrapper. One can use it as follows:

```
import glisten
log = glisten.log.Logger('.log')

@log.deprecate
def my_deprecated_function():
    return
```

Any time this function is called, glisten will output `Function "my_deprecated_function" is deprecated.`, and log it to file.