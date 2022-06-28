# Computer Architecture & Real-Time Operating System

## Contents for Computer Architecture
1. [Data Representation](#1-Data-Representation)
2. [Building and Loading Programs]
3. [Processor Architecture]
4. [Memory Subsystem]
5. [I/O Devices]
6. [Advanced Computer Architecture]

## Contents for Operating System(RTOS)
1. [Process Management]
2. [Process Scheduling]
3. [Virtual Meomory]
4. [Inter-Process Communication]
5. [Multithreading]
6. [Locking]
7. [Filesystem]
8. [Device Driver]
9. [Real-Time Scheduling]

## 1. Data Representation
Computer system에는 다양한 종류의 데이터가 존재한다.  

1.Bit: 컴퓨터에서 데이터의 가장 작은 유닛, 0과 1 두개 중에 하나를 가진다. 이를 통해서 2가지 표현이 가능  
2.Byte: 8개의 인접한 bit sequence(8bit), 2^8(256)개 의 다른 상태를 표현할 수 있다. Can store a single character, The unit of memory addressing  
3.Word: 2개의 인접한 bytes(16bit) 2^16개의 다른 상태 표현 가능, Another meaning of word: "the natural data size of a processor"  
4.DWord: 2개의 인접한 Word(32bit) 2^32개의 상태 표현 가능  

### Integer Representation
컴퓨터에서 Binary notation(2진법)이 비트를 사용하는 자연스러운 방법  
n개의 비트를 이용해서 2^n개의 mapping을 하여 숫자들을 표현할 수 있다.  

정수 데이터 타입 
 <p align="center">
 <img width="550" src="image/IMG_0056.jpeg">
 </p>

#### Mapping for Unsigned Types
하나의 byte는 256개의 서로다른 상태를 나타낸다. 그렇다면 우리는 이 8개의 비트를 2진수로 해석할 수 있다.
#### Signed Types : Naïve methood
8개의 비트중 가장 앞의 비트를 이용해서 (0:양수, 1:음수)를 결정하고 뒤 7개 비트를 이용해서 표현한다.
<p align="center">
<img width="550" src="image/IMG_0057.jpeg">
</p>  
문제점 : 0000과 1000이 모든 0을 의미함 (낭비)  

#### Signed Types : Two's Complement Method
MSB가 0이면 이것을 그대로 해석하고 MSB가 1이라면 0과 1을 바꾼뒤 +1을 해서 해석한다. (이를 통해 Naïve method 문제점 해결)
<p align="center">
 <img width="550" src="image/IMG_0058.jpeg">
 </p>

#### Byte Ordering
Little-Endian Ordering e.g.) Intel CPUs
Big-Endian Ordering e.g.) Most ARM CPUs
<p align="center">
 <img width="550" src="image/IMG_0059.jpeg">
 </p>

#### Integer Overflow and Underflow
Overflow : data type의 범위를 넘어서면 ex) $11111111_2$ -> +1 -> $00000000_2$     
Underflow : data type의 범위를 내려가면 ex) $00000000_2$ -> -1 -> $11111111_2$

#### Hex code
하나의 byte를 2개의 4-bit로 나눠 16진법으로 표현한다. ex) unsigned char u = $01011111_2$ -> unsigned char u = 0x5F

### Real Number Representation
아무리 작은 범위를 잡아도 그곳에는 무수히 많은 실수가 존재한다. 컴퓨터에서는 n개의 비트를 이용해 2^n개의 정확한 수를 나타낼 수 있다. 
#### Inaccuracy of "Floating-Point Numbers"
컴퓨터 시스템에서 실수를 근사화한 것을 Floating point number라고 한다. 
#### IEEE 754 Standard for Floating-Point Numbers
float:32bits, double: 64bits, 전부 다 signed data types이고 모든 컴파일러에서 같다. 
<p align="center">
 <img width="550" src="image/IMG_0060.jpeg">
 </p>
#### Floating Point Data Types
<p align="center">
 <img width="550" src="image/IMG_0061.jpeg">
 </p>
### Characters Representation
컴퓨터는 오직 숫자만 나타낼 수 있다, 그렇다면 글자는 어떻게 해야할까? 숫자와 글자의 1대1 대응을 통해서
#### 아스키코드 (ASCII Code)
<p align="center">
 <img width="550" src="image/IMG_0062.jpeg">
 </p>
#### String
character들과 마지막 Null character를 묶음.
#### 유니코드(Unicode)
ASCII코드에서 전세계 언어를 저장하기 위해서 유니코드로 확장되어짐. 1개의 바이트로는 유니코드를 저장할 수 없어서 멀티 바이트를 사용

### Multimidea Data
Multimedia Data : 이미지 해상도의 색상코드로 표현되는 픽셀 시퀀스   
Color Depth : 픽셀마다 할당된 bit 
<p align="center">
 <img width="550" src="image/IMG_0063.jpeg">
 </p>
