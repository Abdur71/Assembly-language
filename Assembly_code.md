# Assembly Code 
Here I'm use EMU8086 emuliator. Here I add basic code and try to continous adding.
Happy Coding :sunglasses:

# Basic Structure of Assembly:
### Code
```
.model small
.stack 100h
.data
    
.code
main proc
   
main endp
end main
```
    

# Print any Char in assembly:
### Code
```
.model small
.stack 100h
.data
.code 

main proc
     mov ah, 2h
     mov dl, 'H'
     int 21h
     
main endp
end main
```
Using this code we can print `Hello world!` character by character.

# Print Hello world using string
### Code
```
.model small
.stack 100h

.data
    msg db 'Hello world! $'    
.code 

main proc
     mov ax, @data
     mov ds, ax
     
     mov ah,9
     lea dx, msg
     int 21h
     
     mov ah,4ch
     int 21h
     
main endp
end main
```
In this code we should remeber that in `mov ah, 9` part we use `9` for `string output`. Besides we can use `1` for `single character input`, `2` `single char output`.
Here we use `lea` this means `Load effective register`
