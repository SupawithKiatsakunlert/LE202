## โปรแซสเซสเซอร์ (processor,microcontroller)
ไม่โครคอนโทรลเลอร์ หรือ ที่เรียกกันว่า คอมพิวเตอร์ขนาดเล็ก ซึ่งจะบรรจุความสามารถที่คล้ายกับคอมพิวเตอร์ โดยจะประกอบไปด้วย CPU
หน่วยความจำ ช่องทางเดินของสัญญาณหรือบัส และ วงจรกำเนิดสัญญาณนาฬิกา
## ภาษาชั้นสูง (high level language)
เป็นภาษาโปรแกรมที่ให้โปรแกรมเมอร์เขียนซึ่งเป็นอะไรที่เขียนและสามารถที่จะแปลงง่าย ซึ่งการติดตั้งเป็นอะไรที่ง่ายมาก และ สามารถที่จะนำภาษาไปใช้ได้หลากหลายมาก ยกตัวอย่างเช่น Java, C, C++, Python และอีกมากมาย
## ภาษาแอสเซ็มบลี้ (low level language, assembly)
เป็นภาษาโปรแกราที่ออกแบบเฉพาะเจาะจงเพื่อให้เหมาะแต่ละ Processor เนื่องจาก แต่ละจะมีภาษาเฉพาะเป็นของตัวเอง ยกตัวอย่าง x86 processors 
## ภาษาเครื่อง (machine language)
Manchine Language หรือที่เรียกอีกอย่างคือ ภาษาชั้นต่ำ (Low-Level Languages)ในอีกรูปแบบนึงซึ่งเป็นภาษาที่ตัวของเครื่องจะเข้าใจซึ่งจะเป็นภาษาสูงต่ำ หรือที่เรียกว่า Binary digits เช่น 010000001 ใน Mancine Code จะแปลงเป็น A บนหน้าจอของเรา
# ความสัมพันธ์ ระหว่าง ภาษาชั้นสูง และ ภาษาแอสเซ็มบลี้
## ตัวอย่าง ของ Processor 
# Power64 AT 12.0 
โดยสามารถเเขียนภาษา C+ ยกตัวอย่างเช่น 
int square(int num) {
    return num * num;
}
สามารถแปลงเป็น Low level Language ได้คือ 
square(int):
        .quad   .L.square(int),.TOC.@tocbase,0
.L.square(int):
        std 31,-8(1)
        stdu 1,-64(1)
        mr 31,1
        mr 9,3
        stw 9,112(31)
        lwz 10,112(31)
        lwz 9,112(31)
        mullw 9,10,9
        extsw 9,9
        mr 3,9
        addi 1,31,64
        ld 31,-8(1)
        blr
        .long 0
        .byte 0,9,0,0,128,1,0,1
# JDK 17.0.0
สามารถเขียน java
class Square {
    static int square(int num) {
        return num * num;
    }
}
และแปลงเป็น Low level Language ได้คือ 
class Square {
  Square();
       0: aload_0
       1: invokespecial #1                  // Method java/lang/Object."<init>":()V
       4: return


  static int square(int);
       0: iload_0
       1: iload_0
       2: imul
       3: ireturn

}
