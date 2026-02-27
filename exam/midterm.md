

## ข้อสอบกลางภาค — เลือกตอบ 40 ข้อ (A–D)


**1)** ข้อใด “ใกล้เคียงที่สุด” กับนิยาม Big Data แบบที่มองเป็น “ข้อจำกัดของระบบ”
A) ข้อมูลที่มีขนาดเกิน 1GB เสมอ
B) ข้อมูลที่ Excel เปิดไม่ได้เท่านั้น
C) ข้อมูลที่ทำให้วิธีเดิม ๆ (เครื่องเดียว/เครื่องมือเดิม) จัดเก็บ–ประมวลผล–วิเคราะห์ไม่ไหว ต้องเปลี่ยนสถาปัตยกรรม
D) ข้อมูลที่เป็น NoSQL เท่านั้น

**2)** ข้อใด “ไม่ใช่” หนึ่งใน 5Vs
A) Velocity
B) Variability
C) Veracity
D) Volume

**3)** ตัวอย่างที่สะท้อน “Variety” ได้ดีที่สุดคือข้อใด
A) Log เว็บ + รูปภาพ + ข้อความรีวิว + พิกัด GPS ต้องวิเคราะห์ร่วมกัน
B) ไฟล์ CSV มี 200 ล้านแถว
C) ข้อมูลเข้ามาทุก 1 วินาที
D) ข้อมูลมีค่า missing เยอะ

**4)** ทำไม “Data Pipeline” จึงจำเป็นในงาน Big Data
A) เพื่อทำให้ข้อมูลทุกอย่างเป็นรูปภาพ
B) เพื่อแปลงข้อมูลดิบให้เป็นข้อมูลที่พร้อมใช้งาน/เชื่อถือได้ ผ่านขั้น ingest→clean→transform→store→analyze
C) เพื่อทำให้ทุกคนใช้ Excel ได้เร็วขึ้น
D) เพื่อแทนที่ฐานข้อมูลทั้งหมด

**5)** บริษัท e-commerce แห่งหนึ่งเริ่มเก็บข้อมูลเพิ่ม: clickstream จากเว็บแบบ real-time, รูปภาพรีวิวสินค้า, แชตลูกค้า, และ log จากหลายประเทศ แต่ทีม data เจอปัญหา “นิยามข้อมูลไม่เหมือนกัน, สคีมาเปลี่ยนบ่อย, ค่าซ้ำ/ค่าว่างเยอะ, แหล่งข้อมูลขัดแย้งกัน” ทำให้รายงานยอดขายแต่ละแผนกไม่ตรงกัน
ปัญหาหลักเข้ากับ V ใดมากที่สุด
A) Volume + Velocity
B) Variety + Value
C) Veracity + Variability
D) Volume + Variety

**6)** “Columnar Storage” เหมาะกับงานวิเคราะห์ (analytics) เพราะอะไร
A) เขียนข้อมูลได้เร็วกว่าเสมอ
B) อ่านเฉพาะบางคอลัมน์ได้ ลด I/O และรองรับการบีบอัดดี
C) ทำให้ข้อมูลเป็น JSON อัตโนมัติ
D) ไม่ต้องมี schema

**7)** ปัญหา “Small Files Problem” มักเกิดหนักในระบบแบบใด และเพราะอะไร
A) เกิดเฉพาะในเครื่อง local เพราะ SSD ช้า
B) เกิดใน distributed/object storage เพราะค่าใช้จ่าย/เวลาไปติดที่ metadata และการจัดการไฟล์จำนวนมาก
C) เกิดเฉพาะในไฟล์ Parquet เพราะ columnar
D) ไม่เกี่ยวกับจำนวนไฟล์ เกี่ยวกับขนาดไฟล์อย่างเดียว

**8)** ข้อใดใกล้เคียง “HDFS vs S3” มากที่สุด
A) HDFS เป็น object storage, S3 เป็น distributed filesystem
B) HDFS มักมี metadata/namespace แบบศูนย์กลาง (เช่น NameNode) และทำงานเป็น filesystem, S3 เป็น object storage เน้น key/object
C) ทั้งสองเหมือนกัน ต่างกันแค่ราคา
D) S3 ใช้ไม่ได้กับ Spark

**9)** ข้อใดอธิบาย “แนวคิดหลักของ Parquet” ได้ถูกต้องที่สุด
A) เป็นไฟล์ข้อความ (text) ที่อ่านง่ายและรองรับ schema แบบหลวม
B) เป็นไฟล์แบบ columnar เก็บข้อมูลเป็น row groups/column chunks พร้อม metadata/สถิติ ช่วยให้ engine ทำ column pruning และ predicate pushdown ได้
C) เป็น format สำหรับเก็บ key-value บน object storage เท่านั้น
D) เป็นฐานข้อมูลที่รองรับ ACID ในตัวโดยไม่ต้องมี table format

**10)** ข้อใดเป็นปัญหาคลาสสิกของ CSV ที่ทำให้ parsing พัง
A) มี schema ชัดเจนเกินไป
B) มี comma/quote ในข้อความ แต่กำหนด quotechar/escape ไม่ถูก
C) ใช้ไม่ได้กับ pandas
D) บีบอัดไม่ได้

**11)** ถ้าต้องการ “อ่านเฉพาะคอลัมน์ status จาก Parquet” ใน pandas วิธีที่เหมาะคือข้อใด
A) `pd.read_csv("data.parquet")`
B) `pd.read_parquet("data.parquet", columns=["status"])`
C) `open("data.parquet").read()`
D) `pd.read_parquet("data.parquet", usecols=["status"])`

**12)** การเลือก compression สำหรับ Parquet มัก trade-off อะไร
A) ความถูกต้อง vs ความผิดพลาด
B) ขนาดไฟล์เล็กลง vs เวลาเขียน/อ่าน (ขึ้นกับ codec และ workload)
C) จำนวนคอลัมน์ vs จำนวนแถว
D) schema vs ไม่มี schema

**13)** บริษัทมีข้อมูล 3 แบบ:
(1) ข้อมูลธุรกรรมที่ต้องทำรายงาน CFO ทุกวัน (ต้องคุมคุณภาพ/สคีมา)
(2) ข้อมูลดิบจำนวนมาก (log, รูป, json) ที่อยากเก็บก่อน เผื่ออนาคต
(3) ทีม data science อยาก query/ทำ feature จากข้อมูลดิบ+ข้อมูล curated ในที่เดียว และต้องมี governance/ACID บางส่วน
การเลือกแนวทาง “ที่เหมาะที่สุด” คือข้อใด
A) Warehouse สำหรับ (1), Lake สำหรับ (2), Lakehouse สำหรับ (3)
B) Lake อย่างเดียวพอ เพราะถูกสุดและยืดหยุ่นสุด
C) Warehouse อย่างเดียวพอ เพราะ query เร็วสุด
D) Lakehouse อย่างเดียวพอเสมอ ไม่ต้องแยกชั้นข้อมูล

**14)** **(เติมโค้ด 3 ช่องว่าง)** ต้องการอ่าน Parquet ด้วย PyArrow และอ่านแค่ 2 คอลัมน์

```python
import pyarrow.parquet as pq
pf = pq.ParquetFile("data.parquet")
subset = pf.read(columns=[______[1], ______[2]]).______[3]()
```

ตัวเลือก
A) `[1]="status",[2]="value",[3]=to_pandas`
B) `[1]="status",[2]="value",[3]=to_csv`
C) `[1]="status",[2]="value",[3]=df`
D) `[1]="Status",[2]="Value",[3]=to_pandas`

**15)** ถ้าต้อง “ลด small files” แนวทางที่เหมาะที่สุดคือข้อใด
A) แตกไฟล์ให้ย่อยลงอีกเพื่อ parallelism
B) รวมไฟล์ (compaction) และกำหนดขนาดไฟล์เป้าหมาย + partition ที่พอดี
C) เปลี่ยนจาก Parquet เป็น CSV
D) ปิดการทำ partition ทั้งหมดเสมอ

**16)** แนวโน้ม “วิวัฒนาการของ SQL” ในยุค Big Data/Cloud ที่ถูกต้องที่สุดคือข้อใด
A) SQL ใช้ได้เฉพาะ RDBMS แบบเครื่องเดียวเท่านั้น
B) SQL กลายเป็นภาษากลางของ analytics: ใช้ได้ทั้งใน data warehouse, distributed engine, และ query บนไฟล์ (เช่น Parquet) ผ่าน query engine
C) SQL ถูกแทนที่หมดโดย NoSQL จึงไม่จำเป็นต้องเรียน
D) SQL เหมาะกับงาน OLTP เท่านั้น ใช้กับ analytics ไม่ได้

**17)** ข้อใดสะท้อน “การขยายขีดความสามารถของ SQL” ได้ชัดที่สุดในยุคใหม่
A) SQL ไม่มีมาตรฐานแล้ว ทุกค่ายใช้คำสั่งเหมือนกันหมด
B) SQL เพิ่มความสามารถเชิงวิเคราะห์มากขึ้น เช่น window functions, CTE, รวมถึงการเชื่อมกับ UDF/engine ที่รันแบบ distributed
C) SQL ยกเลิก JOIN เพราะช้าเกินไป
D) SQL บังคับให้ทุกข้อมูลต้องเป็น 3NF เสมอ

**18)** ข้อใดคือเหตุผลหลักที่ Parquet มักเร็วกว่า CSV สำหรับงาน “filter + aggregate”
A) Parquet เป็นไฟล์ข้อความอ่านง่าย
B) Parquet มี metadata/สถิติ/column pruning ช่วยลดการอ่านข้อมูลที่ไม่จำเป็น
C) CSV ถูกบีบอัดไม่ได้
D) CSV ห้ามมี header

**19)** เลือกลำดับ “SQL Logical Order of Execution” ที่ถูกต้อง
A) SELECT → FROM → WHERE → GROUP BY → HAVING → ORDER BY → LIMIT
B) FROM → WHERE → GROUP BY → HAVING → SELECT → ORDER BY → LIMIT
C) FROM → SELECT → WHERE → GROUP BY → HAVING → ORDER BY → LIMIT
D) WHERE → FROM → GROUP BY → HAVING → SELECT → ORDER BY → LIMIT

สมมติว่ามีตารางชื่อ housing (California house price) มีคอลัมน์หลัก เช่น
longitude, latitude, housing_median_age, total_rooms, total_bedrooms, population, households, median_income, median_house_value, ocean_proximity

**20)** (เติม 3 ช่องว่าง) ต้องการ “ค่าเฉลี่ยราคา (median_house_value) ราย ocean_proximity” เฉพาะกลุ่มที่มีจำนวนแถว ≥ 500 และเรียงจากแพงไปถูก

SELECT ocean_proximity,
       ______[1](median_house_value) AS avg_price,
       ______[2](*) AS n
FROM housing
GROUP BY ocean_proximity
HAVING ______[2](*) >= 500
ORDER BY avg_price ______[3];

A) [1]=AVG [2]=COUNT [3]=DESC
B) [1]=COUNT [2]=AVG [3]=DESC
C) [1]=AVG [2]=SUM [3]=ASC
D) [1]=SUM [2]=COUNT [3]=ASC

**21)** (เติม 3 ช่องว่าง) ต้องการสร้าง “income_band” เป็น 3 ระดับ แล้วนับจำนวนบ้านในแต่ละ band

low: median_income < 2

mid: 2 ≤ median_income < 5

high: ≥ 5

SELECT
  CASE
    WHEN median_income < 2 THEN 'low'
    WHEN median_income < 5 THEN 'mid'
    ELSE ______[1]
  END AS income_band,
  ______[2](*) AS n
FROM housing
GROUP BY ______[3];

A) [1]='high' [2]=COUNT [3]=income_band
B) [1]='HIGH' [2]=SUM [3]=median_income
C) [1]=high [2]=COUNT [3]=CASE
D) [1]='high' [2]=AVG [3]=income_band

**22)** (เติม 3 ช่องว่าง) กรองแถวที่ total_bedrooms เป็น null หรือ ≤ 0 ออก และตัด ocean_proximity = 'ISLAND' จากนั้นสร้างคอลัมน์ value_per_bedroom และหาค่าเฉลี่ย

from pyspark.sql import functions as F

out = (housing_df
  .filter( ______[1] )
  .withColumn("value_per_bedroom", ______[2] )
  .agg( ______[3] )
)

A)
[1] (F.col("total_bedrooms").isNotNull()) & (F.col("total_bedrooms") > 0) & (F.col("median_house_value").isNotNull()) & (F.col("ocean_proximity") != "ISLAND")
[2] F.col("median_house_value") / F.col("total_bedrooms")
[3] F.avg("value_per_bedroom").alias("avg_value_per_bedroom")

B)
[1] (F.col("total_bedrooms").isNull()) | (F.col("total_bedrooms") <= 0)
[2] F.col("total_bedrooms") / F.col("median_house_value")
[3] F.sum("value_per_bedroom")

C)
[1] (F.col("ocean_proximity") == "ISLAND")
[2] F.col("median_house_value") / F.col("total_rooms")
[3] F.count("*")

D)
[1] (F.col("median_house_value").isNull())
[2] F.col("median_house_value") / F.col("total_bedrooms")
[3] F.avg("median_house_value")

**23)** (เติม 3 ช่องว่าง) สร้าง lat1 = round(latitude, 1) แล้วหาค่าเฉลี่ย median_house_value ต่อ lat1 พร้อมนับจำนวนแถว เลือกเฉพาะกลุ่มที่ n >= 200 เรียงจาก avg_price มากไปน้อย เอา 5 อันดับแรก

from pyspark.sql import functions as F

top5 = (housing_df
  .filter(F.col("median_house_value").isNotNull())
  .withColumn("lat1", ______[1] )
  .groupBy("lat1")
  .agg(
      ______[2],
      F.count("*").alias("n")
  )
  .filter(F.col("n") >= 200)
  .orderBy(F.col("avg_price").desc())
  .limit( ______[3] )
)

A)
[1] F.round(F.col("latitude"), 1)
[2] F.avg("median_house_value").alias("avg_price")
[3] 5

B)
[1] F.ceil(F.col("latitude"))
[2] F.sum("median_house_value").alias("avg_price")
[3] "5"

C)
[1] F.round("latitude")
[2] F.avg("median_income").alias("avg_price")
[3] 10

D)
[1] F.floor(F.col("latitude"), 1)
[2] F.count("median_house_value").alias("avg_price")
[3] 5

**24)** ข้อใดอธิบาย “DuckDB vs Spark SQL” ได้เหมาะสมที่สุด
A) DuckDB ใช้กับงาน local/ไฟล์ได้ดี, Spark SQL เหมาะกับงานกระจาย/ข้อมูลใหญ่จริง
B) Spark SQL เร็วกว่าเสมอแม้ข้อมูลเล็ก
C) DuckDB ใช้ไม่ได้กับ Parquet
D) ทั้งสองไม่มี optimizer

**25)** ถ้าต้องการเทียบ “เวลาคิวรี” แบบยุติธรรม ควรทำอะไร
A) รันครั้งเดียวพอ
B) รันซ้ำหลายครั้ง แล้วใช้ค่าที่เหมาะสม (เช่น best-of-3) และควบคุม cache/สภาพแวดล้อมเท่าที่ทำได้
C) รันพร้อมเปิดโปรแกรมอื่นหนัก ๆ
D) วัดเวลาจากความรู้สึก

**26)** Spark แตกต่างจาก Hadoop MapReduce อย่างมีนัยสำคัญในข้อใด (แต่ละช้อยมี 3 คุณสมบัติ)
A) Spark: in-memory + DAG/lazy + เหมาะ iterative/interactive / Hadoop MR: disk-heavy per stage + rigid map→reduce + latency สูง
B) Spark: ต้องเขียน Java เท่านั้น + ไม่มี SQL + ไม่รองรับ cluster / Hadoop MR: ทำได้ทุกอย่างแบบ real-time
C) Spark: ใช้ได้เฉพาะไฟล์ CSV + ไม่มี fault tolerance + ไม่มี shuffle / Hadoop MR: มีแค่ HDFS อย่างเดียว
D) Spark: ไม่มี scheduler + ไม่มี lineage + ไม่รองรับ partition / Hadoop MR: เร็วกว่าเสมอทุกงาน

**27)** องค์ประกอบหลักของ Spark ที่ “จัดชุดได้ถูกต้อง” คือข้อใด (3 รายการ/ช้อย)
A) Driver + Executors + Cluster Manager
B) NameNode + DataNode + JobTracker
C) Broker + Topic + Consumer
D) API Gateway + Load Balancer + CDN

**28)** ข้อใดจับคู่ “องค์ประกอบ → หน้าที่” ได้ถูกต้องที่สุด (เลือก 1 ข้อ)
A) Driver → วางแผน DAG/สั่งงาน และรวบรวมผลลัพธ์
B) Executors → เก็บ metadata ของไฟล์ทั้งหมดทั้งคลัสเตอร์ (เหมือน NameNode)
C) Cluster Manager → แปลง SQL เป็นไฟล์ Parquet อัตโนมัติ
D) Driver → รัน task ทั้งหมดบน worker แทน executors

**29)** ข้อใดเป็นตัวอย่าง “Transformation” (lazy)
A) `count()`
B) `collect()`
C) `select()` / `filter()`
D) `show()` (ให้ผลลัพธ์ทันที)

**30)** ข้อใดเป็น “Action” ที่มักทำให้เกิดการคำนวณจริง
A) `withColumn()`
B) `groupBy()`
C) `count()`
D) `select()`

**31)** “Shuffle” ใน Spark มักเกิดตอนใด
A) อ่าน Parquet
B) งานที่ต้องย้ายข้อมูลข้าม partition เช่น join/groupBy ตาม key
C) show 5 แถว
D) rename column

**32)** ทำไมต้องมี “Logical plan” และ “Physical plan”
A) เพื่อให้ SQL อ่านสวยขึ้น
B) Logical = ความตั้งใจ/โครงคิวรี, Physical = วิธีทำจริงที่ optimizer เลือก (เช่น join strategy)
C) เพราะ Spark ไม่มี optimizer
D) เพื่อแทน schema

**33)** **(เติมโค้ด 3 ช่องว่าง)** เติมให้ถูกต้อง: อ่าน Parquet แล้วกรองและนับ

```python
df = spark.read.______[1]("data.parquet")
out = df.______[2](F.col("status") == "Completed").______[3]()
```

ตัวเลือก
A) `[1]=parquet, [2]=filter, [3]=count`
B) `[1]=csv, [2]=select, [3]=show`
C) `[1]=json, [2]=groupBy, [3]=collect`
D) `[1]=parquet, [2]=withColumn, [3]=limit`

**34)** **(เติมโค้ด 3 ช่องว่าง)** สร้าง temp view และใช้ Spark SQL

```python
df.createOrReplaceTempView("t")
res = spark.______[1]("SELECT ______[2] FROM t").______[3]()
```

ตัวเลือก
A) `[1]=sql, [2]=COUNT(*), [3]=show`
B) `[1]=SQL, [2]=SUM(*), [3]=collect`
C) `[1]=query, [2]=COUNT, [3]=display`
D) `[1]=sql, [2]=LIMIT 5, [3]=count`

**35)** ข้อใดสื่อความหมาย “Lazy Evaluation” ได้ตรงที่สุด
A) Spark จะคำนวณทุกบรรทัดทันทีที่เรียก transformation
B) Spark จะสะสมแผนงานไว้ และเริ่มคำนวณเมื่อเจอ action
C) Spark คำนวณช้ากว่าเสมอ
D) Spark ห้ามทำงานแบบ SQL

**36)** Pipeline ขั้น ingest มักเน้นอะไรเป็นพิเศษ
A) ทำ dashboard ทันที
B) ตรวจว่าอ่านเข้าได้จริง + validity เบื้องต้น (schema, corrupt records, types)
C) train model
D) สร้าง index เสมอ

**37)** ในการอ่าน CSV ด้วย Spark แบบ “ดักบรรทัดพัง” แนวคิดที่เหมาะคือข้อใด
A) ไม่ต้องกำหนด schema ปล่อยเดาอย่างเดียว
B) กำหนด schema และมีคอลัมน์ `_corrupt_record` เพื่อจับบรรทัดเสีย + ใช้โหมดอ่านที่เหมาะสม
C) เปลี่ยนไฟล์เป็นรูปภาพก่อน
D) อ่านด้วย Excel แล้วค่อย save

**38)** ข้อใดเป็นตัวอย่าง “Data Quality Dimension” ที่พบบ่อย
A) Completeness / Validity / Accuracy / Uniqueness
B) Brightness / Contrast
C) Latency / Throughput
D) CPU / RAM

**39)** **(เติมโค้ด 3 ช่องว่าง)** จาก pipeline: ตัดบรรทัด corrupt และแทน user_id ที่หายเป็น "UNKNOWN"

```python
step1_df = raw_df \
  .filter(F.col("______[1]").isNull()) \
  .drop("______[2]") \
  .withColumn("user_id",
      F.when(F.col("user_id").isNull(), "______[3]").otherwise(F.col("user_id"))
  )
```

ตัวเลือก
A) `[1]=_corrupt_record, [2]=_corrupt_record, [3]=UNKNOWN`
B) `[1]=corrupt, [2]=corrupt, [3]=NULL`
C) `[1]=transaction_id, [2]=user_id, [3]=UNKNOWN`
D) `[1]=_corrupt_record, [2]=status, [3]=MISSING`

**40)** **(เติมโค้ด 3 ช่องว่าง)** การบันทึก curated data เป็น Parquet แบบ partition

```python
transformed_df.write \
  .mode("______[1]") \
  .partitionBy("______[2]", "______[3]") \
  .parquet(output_path)
```

ตัวเลือก
A) `[1]=overwrite, [2]=tier, [3]=status`
B) `[1]=append, [2]=amount, [3]=date`
C) `[1]=ignore, [2]=user_id, [3]=transaction_id`
D) `[1]=overwrite, [2]=running_total, [3]=txn_sequence_number`
