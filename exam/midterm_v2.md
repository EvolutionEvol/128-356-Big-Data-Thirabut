

## ข้อสอบกลางภาค (ชุดที่ 2) — เลือกตอบ 40 ข้อ (A–D)


**1)** ข้อใดอธิบาย "Big Data" ในเชิงสถาปัตยกรรมได้ดีที่สุด
A) ข้อมูลที่มีจำนวนแถวเกิน 10 ล้านแถว
B) ข้อมูลที่ต้องใช้ระบบกระจาย (distributed system) เพราะเครื่องเดียวหรือเครื่องมือเดิมจัดการไม่ไหว
C) ข้อมูลที่ต้องเก็บใน cloud เท่านั้น
D) ข้อมูลที่เป็น unstructured ทุกประเภท

**2)** ข้อใด "ไม่ใช่" มิติของ 5Vs ของ Big Data
A) Volume
B) Visibility
C) Velocity
D) Value

**3)** ตัวอย่างที่สะท้อน "Velocity" ได้ดีที่สุดคือข้อใด
A) ข้อมูลมาจากหลายรูปแบบ เช่น CSV, JSON, รูปภาพ
B) ข้อมูล sensor ในโรงงานส่งค่าทุก 100 มิลลิวินาที ต้องประมวลผลแบบ near real-time
C) ข้อมูลมียอด duplicate 20%
D) ข้อมูลรวมกว่า 1 PB แต่ไม่มีใครนำไปใช้

**4)** ขั้นตอนใดของ Data Pipeline ทำหน้าที่ตรวจสอบคุณภาพข้อมูลและแปลงรูปแบบ
A) Ingest
B) Transform / Clean
C) Store
D) Visualize

**5)** ร้านค้าออนไลน์รายหนึ่งเก็บ log การใช้งานจากแอปมือถือ (JSON), ข้อมูลการชำระเงิน (structured database), รีวิวสินค้าเป็นข้อความ (text), และภาพสินค้า (image) แต่ทีม data ไม่สามารถรวมข้อมูลเข้าด้วยกันได้ เพราะแต่ละแหล่งมีรูปแบบต่างกัน
ปัญหาหลักเข้ากับ V ใดมากที่สุด
A) Volume
B) Variety
C) Velocity
D) Value

**6)** ข้อใดเป็นข้อดีหลักของ "Row-based Storage" เทียบกับ Columnar Storage
A) อ่านเฉพาะบางคอลัมน์ได้เร็วกว่า
B) เขียนข้อมูลแถวใหม่ (INSERT) ได้เร็วกว่า เพราะเก็บข้อมูลทั้งแถวรวมกัน
C) บีบอัดได้ดีกว่าเสมอ
D) ไม่ต้องมี primary key

**7)** "Small Files Problem" ส่งผลกระทบอย่างไรต่อ HDFS
A) ทำให้ NameNode ต้องเก็บ metadata จำนวนมากจนหน่วยความจำเต็ม และ I/O overhead เพิ่มขึ้น
B) ทำให้ DataNode ไม่สามารถเก็บไฟล์ได้เลย
C) ทำให้ replication factor ลดลง
D) ทำให้ block size เล็กลงอัตโนมัติ

**8)** ข้อใดเปรียบเทียบ "Data Lake vs Data Warehouse" ได้ถูกต้อง
A) Data Lake เก็บเฉพาะข้อมูล structured, Data Warehouse เก็บทุกรูปแบบ
B) Data Lake เก็บข้อมูลดิบทุกรูปแบบ (schema-on-read), Data Warehouse เก็บข้อมูลที่ผ่านการ curate แล้ว (schema-on-write)
C) ทั้งสองเหมือนกัน ต่างกันแค่ชื่อ
D) Data Warehouse ถูกกว่า Data Lake เสมอ

**9)** ข้อใดอธิบาย "Parquet Row Group" ได้ถูกต้อง
A) เป็นกลุ่มของแถวทั้งหมดในไฟล์ที่ถูกจัดเรียงตาม primary key
B) เป็นหน่วยย่อยที่แบ่งข้อมูลออกเป็นชุด โดยแต่ละ row group มี column chunk แยกกัน พร้อม statistics สำหรับ predicate pushdown
C) เป็น index ที่ Parquet สร้างอัตโนมัติสำหรับทุกคอลัมน์
D) เป็นส่วนของ footer ที่เก็บ schema เท่านั้น

**10)** ข้อใดเป็นข้อจำกัดของ CSV ที่ทำให้ไม่เหมาะกับงาน analytics ขนาดใหญ่
A) CSV มี schema ที่เข้มงวดเกินไป
B) CSV ไม่มี schema ในตัว ไม่รองรับ column pruning และบีบอัดได้ไม่ดีเท่า columnar format
C) CSV ใช้ได้เฉพาะกับ Python
D) CSV ไม่สามารถเก็บข้อมูลตัวเลขได้

**11)** ถ้าต้องการอ่าน Parquet ด้วย pandas แล้วกรองเฉพาะแถวที่ `status == "active"` วิธีที่มีประสิทธิภาพที่สุดคือข้อใด
A) `pd.read_parquet("data.parquet", filters=[("status", "==", "active")])`
B) `pd.read_csv("data.parquet").query("status == 'active'")`
C) `pd.read_parquet("data.parquet")` แล้วค่อย `.query()`
D) `open("data.parquet").readlines()`

**12)** Parquet Codec ใดที่มักให้ "compression ratio" ดีที่สุดแต่ช้ากว่าในการเขียน
A) Snappy
B) GZIP/ZSTD
C) ไม่มี codec ใดบีบอัดได้เลย
D) LZ4 เสมอ

**13)** บริษัทต้องการ:
(1) ทำ dashboard real-time สำหรับ CEO ด้วยข้อมูลที่ curate แล้ว
(2) เก็บ raw data ทุกรูปแบบจาก IoT sensor ไว้เพื่อวิเคราะห์ในอนาคต
(3) ทีม ML ต้องการ query ข้อมูลดิบพร้อม ACID support
สถาปัตยกรรมที่เหมาะที่สุดคือข้อใด
A) ใช้ Data Lake อย่างเดียว
B) ใช้ Data Warehouse อย่างเดียว
C) Warehouse สำหรับ (1), Lake สำหรับ (2), Lakehouse สำหรับ (3)
D) ใช้ Spreadsheet เพราะง่ายที่สุด

**14)** **(เติมโค้ด 3 ช่องว่าง)** อ่าน Parquet ด้วย pandas เลือก 3 คอลัมน์ แล้วดูข้อมูล 5 แถวแรก

```python
import pandas as pd
df = pd.______[1]("data.parquet", ______[2]=["id", "name", "score"])
df.______[3]()
```

ตัวเลือก
A) `[1]=read_parquet, [2]=columns, [3]=head`
B) `[1]=read_csv, [2]=usecols, [3]=tail`
C) `[1]=read_parquet, [2]=fields, [3]=show`
D) `[1]=load, [2]=columns, [3]=head`

**15)** วิธีใดช่วยลด Small Files Problem ได้ดีที่สุด
A) เพิ่มจำนวน partition ให้มากขึ้น
B) ใช้ compaction รวมไฟล์เล็กๆ เข้าด้วยกัน พร้อมกำหนด target file size ที่เหมาะสม
C) แปลงจาก Parquet เป็น JSON
D) ลด replication factor ลงเหลือ 1

**16)** ข้อใดอธิบาย "Lakehouse" ได้ตรงที่สุด
A) เป็น Data Lake ที่ไม่มี governance
B) เป็นสถาปัตยกรรมที่รวมข้อดีของ Data Lake (ความยืดหยุ่น, ต้นทุนต่ำ) กับ Data Warehouse (ACID, governance, performance) เข้าด้วยกัน
C) เป็น Warehouse ที่เก็บเฉพาะไฟล์ CSV
D) เป็น NoSQL database ประเภทหนึ่ง

**17)** ข้อใดเป็นตัวอย่างของ "Window Function" ใน SQL
A) `COUNT(*)`
B) `ROW_NUMBER() OVER (PARTITION BY dept ORDER BY salary DESC)`
C) `GROUP BY department`
D) `WHERE salary > 50000`

**18)** ข้อใดอธิบาย "Predicate Pushdown" ได้ถูกต้อง
A) เป็นการ push ข้อมูลทั้งหมดเข้า memory ก่อนแล้วค่อยกรอง
B) เป็นการส่ง filter condition ลงไปที่ชั้น storage เพื่อลดปริมาณข้อมูลที่ต้องอ่านขึ้นมา
C) เป็นการ sort ข้อมูลก่อน filter
D) เป็นการ replicate ข้อมูลทุก node ก่อน query

**19)** ข้อใดเรียงลำดับ "SQL Writing Order" ได้ถูกต้อง
A) FROM → SELECT → WHERE → GROUP BY → HAVING → ORDER BY
B) SELECT → FROM → WHERE → GROUP BY → HAVING → ORDER BY → LIMIT
C) FROM → WHERE → SELECT → GROUP BY → HAVING → ORDER BY
D) SELECT → WHERE → FROM → GROUP BY → ORDER BY → LIMIT

สมมติว่ามีตารางชื่อ employees มีคอลัมน์หลัก เช่น
emp_id, name, department, salary, hire_date, status, office_location, performance_score

**20)** (เติม 3 ช่องว่าง) ต้องการ "จำนวนพนักงาน และเงินเดือนเฉลี่ย ต่อแผนก" เฉพาะแผนกที่มีพนักงาน ≥ 10 คน เรียงเงินเดือนเฉลี่ยจากมากไปน้อย

SELECT department,
       ______[1](*) AS emp_count,
       ______[2](salary) AS avg_salary
FROM employees
WHERE status = 'active'
GROUP BY department
HAVING ______[1](*) >= 10
ORDER BY avg_salary ______[3];

A) [1]=COUNT [2]=AVG [3]=DESC
B) [1]=SUM [2]=AVG [3]=ASC
C) [1]=COUNT [2]=SUM [3]=DESC
D) [1]=AVG [2]=COUNT [3]=ASC

**21)** (เติม 3 ช่องว่าง) ต้องการสร้าง "performance_level" 3 ระดับ แล้วนับจำนวนพนักงานในแต่ละระดับ

low: performance_score < 3

mid: 3 ≤ performance_score < 7

high: ≥ 7

SELECT
  CASE
    WHEN performance_score < 3 THEN 'low'
    WHEN performance_score < 7 THEN 'mid'
    ELSE ______[1]
  END AS performance_level,
  ______[2](*) AS n
FROM employees
GROUP BY ______[3];

A) [1]='high' [2]=COUNT [3]=performance_level
B) [1]='HIGH' [2]=SUM [3]=performance_score
C) [1]=high [2]=COUNT [3]=CASE
D) [1]='high' [2]=AVG [3]=performance_level

**22)** (เติม 3 ช่องว่าง) กรองแถวที่ salary เป็น null หรือ ≤ 0 ออก และตัด status = 'terminated' จากนั้นสร้างคอลัมน์ salary_ratio (= salary / avg ของแผนก) แล้วหาค่าเฉลี่ย salary

from pyspark.sql import functions as F

out = (employees_df
  .filter( ______[1] )
  .groupBy("department")
  .agg( ______[2] )
  .filter( ______[3] )
)

A)
[1] (F.col("salary").isNotNull()) & (F.col("salary") > 0) & (F.col("status") != "terminated")
[2] F.avg("salary").alias("avg_salary"), F.count("*").alias("dept_count")
[3] F.col("dept_count") >= 5

B)
[1] (F.col("salary").isNull()) | (F.col("salary") <= 0)
[2] F.sum("salary").alias("avg_salary")
[3] F.col("avg_salary") > 0

C)
[1] (F.col("status") == "terminated")
[2] F.count("*").alias("avg_salary")
[3] F.col("avg_salary") >= 100000

D)
[1] (F.col("salary").isNotNull())
[2] F.max("salary").alias("avg_salary")
[3] F.col("avg_salary") > 0

**23)** (เติม 3 ช่องว่าง) สร้าง hire_year = year(hire_date) แล้วหาค่าเฉลี่ย salary ต่อ hire_year พร้อมนับจำนวนแถว เลือกเฉพาะปีที่มีพนักงาน >= 50 คน เรียงจาก avg_sal มากไปน้อย เอา 3 อันดับแรก

from pyspark.sql import functions as F

top3 = (employees_df
  .filter(F.col("salary").isNotNull())
  .withColumn("hire_year", ______[1] )
  .groupBy("hire_year")
  .agg(
      ______[2],
      F.count("*").alias("n")
  )
  .filter(F.col("n") >= 50)
  .orderBy(F.col("avg_sal").desc())
  .limit( ______[3] )
)

A)
[1] F.year(F.col("hire_date"))
[2] F.avg("salary").alias("avg_sal")
[3] 3

B)
[1] F.month(F.col("hire_date"))
[2] F.sum("salary").alias("avg_sal")
[3] "3"

C)
[1] F.year("hire_date")
[2] F.avg("performance_score").alias("avg_sal")
[3] 10

D)
[1] F.date_format(F.col("hire_date"), "yyyy")
[2] F.count("salary").alias("avg_sal")
[3] 3

**24)** ข้อใดเป็นเหตุผลที่ "DuckDB ไม่เหมาะกับงาน Big Data ขนาดใหญ่จริง ๆ"
A) DuckDB ไม่รองรับ SQL
B) DuckDB ทำงานบนเครื่องเดียว (single-node) ไม่สามารถ scale out ข้าม cluster ได้
C) DuckDB ไม่สามารถอ่าน Parquet ได้
D) DuckDB ช้ากว่า Excel เสมอ

**25)** ข้อใดเป็นวิธีลด "bias" ในการวัดประสิทธิภาพ query
A) รันบนเครื่องที่ช้าที่สุดเท่าที่หาได้
B) ใช้ warm-up run ก่อน แล้วรันซ้ำหลายครั้งเพื่อลดผลกระทบจาก cache และ system variability
C) รันครั้งเดียวแล้วจดผลทันที
D) ไม่จำเป็นต้องควบคุมสภาพแวดล้อม

**26)** ข้อใดอธิบายข้อดีของ Spark เทียบกับ Hadoop MapReduce ได้ถูกต้อง
A) Spark เร็วกว่าเพราะประมวลผลแบบ in-memory และรวม transformation เป็น DAG ที่ optimize ได้ แทนที่จะเขียน disk ทุกขั้น
B) Spark ใช้ disk มากกว่า MapReduce เพราะ cache ทุกอย่าง
C) MapReduce รองรับ SQL ได้ดีกว่า Spark
D) Spark ไม่มี fault tolerance ต่างจาก MapReduce

**27)** "Spark Execution Hierarchy" จากใหญ่ไปเล็กที่ถูกต้องคือข้อใด
A) Task → Stage → Job → Application
B) Application → Job → Stage → Task
C) Job → Application → Task → Stage
D) Stage → Job → Task → Application

**28)** ข้อใดจับคู่ "Spark Component → หน้าที่" ได้ถูกต้อง
A) Executor → รัน task ที่ได้รับมอบหมายจาก Driver บน worker node และ cache ข้อมูลใน memory
B) Driver → รัน task ทุกตัวเองโดยไม่ส่งงานไปที่ worker
C) Cluster Manager → แปลง DataFrame เป็น RDD อัตโนมัติ
D) Executor → จัดการ metadata ของ HDFS

**29)** ข้อใดเป็น "Transformation" ที่เป็น Wide Transformation (ต้อง shuffle)
A) `filter()`
B) `select()`
C) `groupBy().agg()`
D) `withColumn()`

**30)** ข้อใดเป็น "Action" ที่ทำให้ Spark เริ่มคำนวณจริง
A) `orderBy()`
B) `filter()`
C) `write.parquet()`
D) `withColumnRenamed()`

**31)** ข้อใดอธิบาย "Catalyst Optimizer" ได้ถูกต้อง
A) เป็น library สำหรับทำ machine learning ใน Spark
B) เป็น query optimizer ของ Spark SQL ที่วิเคราะห์ logical plan แล้วสร้าง physical plan ที่มีประสิทธิภาพสูงสุด
C) เป็น storage engine ของ Spark
D) เป็น cluster manager ชนิดหนึ่ง

**32)** ข้อใดอธิบาย "Lineage" ใน Spark ได้ดีที่สุด
A) เป็นการ backup ข้อมูลไปยัง disk เสมอ
B) เป็นการบันทึกลำดับ transformation ทั้งหมดที่สร้าง RDD/DataFrame ขึ้นมา ทำให้สามารถ recompute ได้หาก partition สูญหาย
C) เป็นการ replicate ข้อมูลไป 3 node
D) เป็นการเก็บ log ของ SQL query ทุกตัว

**33)** **(เติมโค้ด 3 ช่องว่าง)** อ่าน CSV แล้วกรองและแสดงผล

```python
df = spark.read.______[1]("data.csv", header=True, inferSchema=True)
out = df.______[2](F.col("amount") > 1000).______[3](10)
```

ตัวเลือก
A) `[1]=csv, [2]=filter, [3]=show`
B) `[1]=parquet, [2]=select, [3]=count`
C) `[1]=text, [2]=groupBy, [3]=collect`
D) `[1]=csv, [2]=withColumn, [3]=limit`

**34)** **(เติมโค้ด 3 ช่องว่าง)** cache DataFrame แล้วใช้ซ้ำ

```python
df.______[1]()
count_val = df.______[2]()
df.______[3](5)
```

ตัวเลือก
A) `[1]=cache, [2]=count, [3]=show`
B) `[1]=persist, [2]=show, [3]=count`
C) `[1]=save, [2]=count, [3]=display`
D) `[1]=cache, [2]=collect, [3]=limit`

**35)** ข้อใดอธิบาย "DAG (Directed Acyclic Graph)" ใน Spark ได้ถูกต้อง
A) เป็นกราฟที่มี cycle เพื่อให้ Spark ทำซ้ำได้
B) เป็นกราฟที่แสดงลำดับ transformation/action โดยไม่มี cycle ช่วยให้ Spark วางแผนและ optimize การทำงานได้
C) เป็นโครงสร้างข้อมูลสำหรับเก็บ graph data เช่น social network
D) เป็น file format ประเภทหนึ่งของ Spark

**36)** ขั้นตอนใดของ Data Pipeline ควรทำ "Data Validation" เช่น ตรวจสอบ schema, data type, null values
A) หลังทำ visualization เสร็จ
B) ในขั้น ingest และ/หรือ transform ก่อนนำข้อมูลไปใช้ต่อ
C) เฉพาะตอน export ข้อมูลออก
D) ไม่จำเป็นต้องทำ validation

**37)** ข้อใดเป็น "best practice" ในการอ่าน CSV ด้วย Spark เพื่อป้องกันปัญหา data quality
A) ไม่ต้องกำหนด schema ปล่อยให้ Spark inferSchema อย่างเดียว
B) กำหนด schema ล่วงหน้า + ใช้ mode="PERMISSIVE" กับ columnNameOfCorruptRecord เพื่อดักข้อมูลผิดรูปแบบ
C) อ่านเฉพาะ 100 แถวแรกเพื่อตรวจสอบ
D) แปลง CSV เป็น JSON ก่อนอ่าน

**38)** ข้อใดอธิบาย "Data Lineage ในบริบทของ Data Pipeline" ได้ดีที่สุด
A) การ compress ข้อมูลให้เล็กลง
B) การติดตามที่มาและการเปลี่ยนแปลงของข้อมูลตลอดทั้ง pipeline ตั้งแต่ต้นทางถึงปลายทาง
C) การ replicate ข้อมูลไปหลาย data center
D) การ encrypt ข้อมูลระหว่างส่ง

**39)** **(เติมโค้ด 3 ช่องว่าง)** กรองข้อมูล null ออก แล้วสร้างคอลัมน์ใหม่และบันทึก

```python
clean_df = raw_df \
  .filter(F.col("______[1]").isNotNull()) \
  .withColumn("______[2]", F.upper(F.col("name"))) \
  .drop("______[3]")
```

ตัวเลือก
A) `[1]=emp_id, [2]=name_upper, [3]=_corrupt_record`
B) `[1]=name, [2]=name_lower, [3]=emp_id`
C) `[1]=salary, [2]=emp_id, [3]=name`
D) `[1]=emp_id, [2]=salary_band, [3]=status`

**40)** **(เติมโค้ด 3 ช่องว่าง)** บันทึกข้อมูลเป็น Parquet แบบ partition ตาม 2 คอลัมน์

```python
result_df.write \
  .mode("______[1]") \
  .partitionBy("______[2]", "______[3]") \
  .parquet(output_path)
```

ตัวเลือก
A) `[1]=overwrite, [2]=department, [3]=hire_year`
B) `[1]=append, [2]=salary, [3]=emp_id`
C) `[1]=ignore, [2]=name, [3]=performance_score`
D) `[1]=overwrite, [2]=emp_id, [3]=office_location`
