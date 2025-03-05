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
Here we use `lea` this means `Load effective register`. Here `4ch` means it handover the contorl to operating system.

# Input output
### Code
```
.model smnall
.stack 100h

.code
main proc
     ;input first number
     mov ah, 1; read char
     int 21h
     mov bl, al ; save char in bl
     
     ;input second number
     mov ah, 1 ; read char
     int 21h
     mov bh, al ; save char in bh
     
     ;print frist number
     mov ah, 2 ; print char
     mov dl, bl
     int 21h 
     
     ;print second number
     mov ah, 2
     mov dl, bh
     int 21h
    
main endp
end main
```
This Assembly code reads two characters from the user, stores them in registers `bl` and `bh`, and then prints them back in the same order. It first sets `ah = 1` to read input using `int 21h`, storing the first character in `bl` and the second in `bh`. Then, it sets `ah = 2`, moves the stored characters to `dl`, and prints them using `int 21h`. If the user inputs `5` and `8`, the output will be `58`.
# To create a new line
### Code
```
     mov ah, 2
     mov dl, 10
     int 21h
     mov dl, 13
     int 21h
```
Write this part to give a new line.
# Add 2 number
### Code
```
.model smnall
.stack 100h

.data
    n1 db ?
    n2 db ?

.code       
main proc
     mov ax, @data
     mov ds, ax 
     
     ;input n1
     mov ah, 1
     int 21h 
     mov bl, al
     sub al, 48
     mov n1, al
     
     ;input n2
     mov ah,1
     int 21h 
     mov bh, al
     sub al, 48
     mov n2, al
     
     ;print newline
     mov ah, 2
     mov dl, 10
     int 21h
     mov dl, 13
     int 21h
     
     ;print n1
     mov ah, 2
     mov dl, bl
     int 21h
     
     ;print + 
     mov ah, 2
     mov dl, '+'
     int 21h 
     
     ;print n2
     mov ah, 2
     mov dl, bh
     int 21h  
     
     ;print =
     mov ah, 2
     mov dl, '='
     int 21h
     
     ;add n1 + n2
     mov dl, n1
     add dl, n2
     add dl, 48  
     mov ah, 2
     int 21h
      
     mov ax, 4ch
     int 21h
    
main endp
end main
```
Here it has some very important code portion. In input n1 `mov bl, al` means when take n1 input subtract `48` to match assci value. In `bl` reserve the `character` and `n1` reserve `value`. It also do in input n2 portion. 
After adding portion add `48` to give the value.