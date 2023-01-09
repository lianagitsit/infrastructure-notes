# Top-down Design

## shell functions

Create additional commands for use in command substitution

Embed mini-scripts in a program with shell functions.

more formal form:
```
function name {
    commands
    return
}
```
or, generally more preferred:
```
name () {
    commands
    return
}
```

Local variables are accessible only within the shell function in which they are defined

Local variables are defined with the keyword `local`

Keep scripts running with stubs, empty functions that include some kind of feedback which shows the logical flow is being carried out

