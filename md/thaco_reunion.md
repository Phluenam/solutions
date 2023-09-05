### Abridged Problem Statement

กำหนดจุด $M$ จุด และวงกลม $N$ วง ต้องการทราบว่าจำเป็นต้องลบวงกลมอย่างน้อยที่สุดกี่วง เพื่อทำให้จุดทุกจุดสามารถลากเส้นไปรวมกันที่จุดใดจุดหนึ่ง โดยที่ไม่ตัดหรือสัมผัสกับวงกลมเลย

### Solution

ก่อนอื่น เริ่มจากการสังเกตว่า คำถามนี้ มีคำตอบเดียวกับคำถามที่ว่า "ลบวงกลมอย่างน้อยที่สุดกี่วง เพื่อให้สามารถลากเส้นเชื่อมระหว่างสองจุดใด ๆ โดยไม่ตัดหรือสัมผัสวงกลม"

เราสังเกตว่า สองจุดใด ๆ จะไปหากันได้ แสดงว่าจะต้องไม่มีวงกลมที่คั่นระหว่างสองจุดนั้น เพื่อความง่ายมากยิ่งขึ้น เรา
สามารถสังเกตวงกลมแต่ละวง สังเกตได้ว่า วงกลมวงหนึ่งจะจำเป็นต้องเอาออก ก็ต่อเมื่อมีบางจุดอยู่ด้านนอกวงกลม
วงนี้และบางจุดอยู่ด้านในวงกลมวงนี้ถ้าหากว่าจุดทุกจุดอยู่ข้างนอก หรือ จุดทุกจุดอยู่ด้านใน เราก็ไม่จำเป็นจะต้องลบ
วงกลมนี้ออกเพื่อให้แต่ละจุดไปหากันได้

ข้อนี้จึงสามารถแก้ได้ด้วยการนับจำนวนวงกลมที่จำเป็นต้องลบออก ดังกล่าว สามารถทำได้ในเวลา $\mathcal{O}(NM)$

### Note

**หมายเหตุ.** ข้อควรระวัง ในการตรวจสอบว่าจุด $P(x_P,y_P)$ อยู่ภายในหรือภายนอกวงกลม $C(x_C,y_C,r_C)$ สามารถ
ตรวจสอบได้ด้วยอสมการ $(x_P-x_C)^2 + (y_P-y_C)^2 < r^2_C$
(หากเป็นจริงถือว่าอยู่ภายในวงกลม หากเป็นเท็จถือว่า
อยู่นอกวงกลม เมื่อรับประกันว่าจุดไม่อยู่บนวงกลม)

*ข้อควรระวังสำคัญคือ การตรวจสอบอสมการดังกล่าวสำหรับค่า* $x_P,y_P,x_C,y_C$ *ระหว่าง* $−10^9$ *ถึง* $10^9$ *และค่า* $r_C$ *ตั้งแต่* $1$ *ถึง* $10^9$ *หากใช้การคูณกันบนข้อมูลชนิด* `int` *หรือจำนวนเต็ม 32 บิต จะทำให้เกิด Integer Overflow และทำให้ คำตอบผิด หากใช้ข้อมูลชนิด* `float` หรือ `double` *จะทำให้เกิดข้อผิดพลาด เนื่องจากข้อมูลตัวเลขประมาณ* $10^{18}$ *จะทำให้ precision ของข้อมูลดังกล่าวไปอยู่ที่ระดับมากกว่า* $10^0$ *(ประมาณ* $10^2$*) มีตัวอย่างตัวอย่างหนึ่งที่จะนำมาแสดงต่อจากนี้ ที่ทำให้การใช้* `double` เกิดปัญหาขึ้น

*วิธีที่แนะนำในข้อนี้คือการใช้ตัวแปรข้อมูลชนิด* `long long` *หรือ* `long double`