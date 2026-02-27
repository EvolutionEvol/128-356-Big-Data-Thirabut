
## ข้อสอบกลางภาค — อัตนัย 4 ข้อ

> **คำชี้แจง:** ให้อธิบายอย่างครบถ้วนและชัดเจน อาจใช้ตัวอย่าง แผนภาพ หรือ pseudo-code ประกอบได้  
> แต่ละข้อ 25 คะแนน (รวม 100 คะแนน)

---

### ข้อที่ 1: วิเคราะห์สถานการณ์จริงด้วย 5Vs (25 คะแนน)

จงอ่านสถานการณ์ต่อไปนี้ แล้ววิเคราะห์ว่าปัญหาที่เกิดขึ้นสอดคล้องกับมิติใดของ **5Vs** (Volume, Velocity, Variety, Veracity, Value) พร้อมอธิบายเหตุผลอย่างละเอียด (แต่ละสถานการณ์อาจสะท้อนมากกว่า 1 มิติ)

---

**สถานการณ์ A (5 คะแนน)**

บริษัทขนส่งแห่งหนึ่งติดตั้ง GPS tracker ในรถทุกคัน จำนวน 10,000 คัน โดย tracker แต่ละตัวส่งพิกัดทุก 3 วินาที ทำให้ระบบเดิมที่ใช้ฐานข้อมูล PostgreSQL บนเครื่องเดียว ประมวลผลไม่ทัน เกิด backlog ยาวขึ้นเรื่อย ๆ และ dashboard แสดงตำแหน่งรถล่าช้าไป 15 นาที

---

**สถานการณ์ B (5 คะแนน)**

โรงพยาบาลต้องการวิเคราะห์ข้อมูลผู้ป่วยเพื่อทำนายความเสี่ยงของโรค โดยต้องนำข้อมูลจากหลายแหล่งมารวมกัน:
- ประวัติการรักษา (ตาราง SQL แบบ structured)
- ภาพ X-ray และ MRI (ไฟล์รูปขนาดใหญ่)
- บันทึกของแพทย์ (ข้อความอิสระภาษาไทย)
- ข้อมูลจาก wearable device ของผู้ป่วย (JSON แบบ semi-structured)

ทีม data engineer พบว่าไม่มี tool ตัวเดียวที่รองรับข้อมูลทุกรูปแบบได้

---

**สถานการณ์ C (5 คะแนน)**

ธนาคารมีระบบตรวจจับ fraud โดยดึงข้อมูลจาก 3 แหล่ง: ระบบ core banking, ระบบบัตรเครดิต, และ partner ภายนอก แต่พบว่า:
- ข้อมูลจากระบบบัตรเครดิตมียอดซ้ำกัน (duplicate) ประมาณ 8%
- ข้อมูลจาก partner มี missing values กว่า 30%
- นิยาม "ธุรกรรมสำเร็จ" ของแต่ละระบบต่างกัน ทำให้ยอดรวมไม่ตรงกัน
- ผลลัพธ์คือ model ตรวจจับ fraud ให้ผลที่ไม่น่าเชื่อถือ

---

**สถานการณ์ D (5 คะแนน)**

บริษัท social media เก็บ log ของ user activity (likes, shares, comments, page views) ทุกวัน ข้อมูลมีรวมกว่า 500 TB ต่อเดือน ทำให้ไม่สามารถ export ออกมาวิเคราะห์ด้วย Excel หรือ pandas บน laptop ได้ และแม้จะย้ายไป server ก็เต็ม disk ภายใน 2 สัปดาห์

---

**สถานการณ์ E (5 คะแนน)**

ร้านค้าออนไลน์เก็บข้อมูล clickstream อย่างละเอียด รวมกว่า 200 TB แต่ไม่เคยนำมาวิเคราะห์ ไม่มี dashboard ไม่ได้ทำ recommendation จนกระทั่ง CEO ถามว่า *"เราเก็บข้อมูลมหาศาลทั้งหมดนี้ไว้ทำไม ใช้ประโยชน์อะไรได้บ้าง?"* ทีม data ตอบไม่ได้ เพราะไม่เคยมีแผนสร้างคุณค่าจากข้อมูลเลย

---

### ข้อที่ 2: Small Files Problem — สาเหตุ, ผลกระทบ, และวิธีแก้ (25 คะแนน)

**คำถาม:**

**(ก)** จงอธิบายว่า **Small Files Problem** คืออะไร เกิดขึ้นได้อย่างไร และทำไมจึงเป็นปัญหาร้ายแรงใน distributed/object storage (เช่น HDFS, S3) โดยอธิบายให้ครอบคลุมเรื่อง metadata overhead และ I/O overhead (10 คะแนน)

**(ข)** จงเสนอวิธีแก้ไข Small Files Problem อย่างน้อย **3 วิธี** โดยแต่ละวิธีต้องอธิบาย:
  1. แนวคิดของวิธีการ
  2. ตัวอย่างการนำไปใช้ (เช่น tool/คำสั่ง/กลยุทธ์)
  3. ข้อจำกัดหรือข้อควรระวัง (15 คะแนน)

---

### ข้อที่ 3: วิเคราะห์ Spark Code — Transformation, Action และ Execution Plan (25 คะแนน)

จงอ่าน PySpark code 3 ชุดต่อไปนี้ แล้วตอบคำถามสำหรับแต่ละชุด

---

#### Code ชุดที่ 1: วิเคราะห์ยอดขายสินค้า

```python
from pyspark.sql import functions as F

# กำหนดตาราง: sales(order_id, customer_id, product, category, amount, order_date, region, status)

df = spark.read.parquet("s3://warehouse/sales/")

step1 = df.filter(F.col("status") == "completed") \
          .filter(F.col("amount") > 0)

step2 = step1.withColumn("amount_band",
    F.when(F.col("amount") < 500, "low")
     .when(F.col("amount") < 5000, "mid")
     .otherwise("high")
)

step3 = step2.groupBy("category", "amount_band") \
             .agg(
                 F.count("*").alias("num_orders"),
                 F.sum("amount").alias("total_revenue"),
                 F.avg("amount").alias("avg_order")
             )

step4 = step3.filter(F.col("num_orders") >= 10) \
             .orderBy(F.col("total_revenue").desc())

step5 = step4.show(20)
```

**(1a)** จงระบุว่าแต่ละ step (step1–step5) เป็น **Transformation** หรือ **Action** พร้อมอธิบายเหตุผลสั้น ๆ (3 คะแนน)

**(1b)** Spark จะเริ่มคำนวณจริง (execute) ตรงไหน? และก่อนหน้านั้น Spark ทำอะไร? (2 คะแนน)

**(1c)** ขั้นตอนใดจะเกิด **Shuffle**? อธิบายว่าทำไมต้องย้ายข้อมูลข้าม partition (2 คะแนน)

---

#### Code ชุดที่ 2: วิเคราะห์พฤติกรรมลูกค้า

```python
from pyspark.sql import functions as F
from pyspark.sql.window import Window

# กำหนดตาราง: transactions(txn_id, customer_id, amount, txn_date, store_id, payment_type)

df = spark.read.parquet("s3://lake/transactions/")

step1 = df.filter(F.col("amount").isNotNull()) \
          .filter(F.col("amount") > 0) \
          .filter(F.col("txn_date") >= "2025-01-01")

step2 = step1.groupBy("customer_id") \
             .agg(
                 F.count("*").alias("total_txns"),
                 F.sum("amount").alias("lifetime_value"),
                 F.avg("amount").alias("avg_txn"),
                 F.max("txn_date").alias("last_txn_date")
             )

step3 = step2.withColumn("customer_tier",
    F.when(F.col("lifetime_value") >= 100000, "platinum")
     .when(F.col("lifetime_value") >= 50000, "gold")
     .when(F.col("lifetime_value") >= 10000, "silver")
     .otherwise("bronze")
)

step4 = step3.filter(F.col("total_txns") >= 5)

step5_count = step4.count()
step5_preview = step4.orderBy(F.col("lifetime_value").desc()).show(10)
```

**(2a)** จงระบุว่าแต่ละ step เป็น Transformation หรือ Action (3 คะแนน)

**(2b)** `step5_count` และ `step5_preview` ทั้งสองเป็น Action — Spark จะรันแผนงาน (DAG) กี่ครั้ง? ทำไม? มีวิธีใดที่จะหลีกเลี่ยงการคำนวณซ้ำ? (3 คะแนน)

---

#### Code ชุดที่ 3: Pipeline จัดเตรียมข้อมูล

```python
from pyspark.sql import functions as F
from pyspark.sql.types import StructType, StructField, StringType, DoubleType, TimestampType

schema = StructType([
    StructField("user_id", StringType()),
    StructField("event_type", StringType()),
    StructField("page_url", StringType()),
    StructField("duration_sec", DoubleType()),
    StructField("event_time", TimestampType()),
    StructField("_corrupt_record", StringType())
])

raw = spark.read.csv("s3://raw/clickstream.csv",
                     header=True, schema=schema,
                     mode="PERMISSIVE",
                     columnNameOfCorruptRecord="_corrupt_record")

step1 = raw.filter(F.col("_corrupt_record").isNull()) \
           .drop("_corrupt_record")

step2 = step1.withColumn("user_id",
    F.when(F.col("user_id").isNull(), "UNKNOWN")
     .otherwise(F.col("user_id"))
)

step3 = step2.withColumn("event_date", F.to_date("event_time")) \
             .withColumn("event_hour", F.hour("event_time"))

step4 = step3.filter(F.col("duration_sec") >= 0)

step5 = step4.write \
             .mode("overwrite") \
             .partitionBy("event_date") \
             .parquet("s3://curated/clickstream/")
```

**(3a)** จงระบุว่าแต่ละ step เป็น Transformation หรือ Action (3 คะแนน)

**(3b)** อธิบายว่าทำไม step1 ถึงกรองด้วย `_corrupt_record` เป็น null? และการ `drop("_corrupt_record")` ทำไปเพื่ออะไร? (2 คะแนน)

**(3c)** `step5` ใช้ `.write.partitionBy("event_date").parquet(...)` — อธิบายว่าการ partition ตาม `event_date` มีประโยชน์อย่างไรต่อการ query ในอนาคต (2 คะแนน)

---

### ข้อที่ 4: ข้อดีและข้อเสียของ Apache Spark (25 คะแนน)

**คำถาม:**

จงอธิบาย **ข้อดี** และ **ข้อเสีย** ของ Apache Spark อย่างละเอียด โดยครอบคลุมหัวข้อต่อไปนี้:

**(ก) ข้อดี (15 คะแนน)** — อธิบายอย่างน้อย 5 ข้อ พร้อมเหตุผลและเปรียบเทียบกับเครื่องมืออื่น (เช่น Hadoop MapReduce, Pandas, DuckDB) ในแต่ละข้อ ตัวอย่างหัวข้อที่ควรกล่าวถึง:

  - In-memory processing และความเร็วเทียบกับ Hadoop MapReduce
  - Unified Engine (SQL, ML, Streaming, Graph ใน platform เดียว)
  - Lazy Evaluation + DAG Optimizer (Catalyst) ช่วยเรื่อง performance อย่างไร
  - Fault Tolerance ผ่าน Lineage / RDD
  - รองรับหลายภาษา (Python, Scala, Java, R, SQL) และ ecosystem ที่กว้าง
  - Scalability (Scale-out จาก laptop ถึง cluster หลายพันเครื่อง)

**(ข) ข้อเสีย (10 คะแนน)** — อธิบายอย่างน้อย 4 ข้อ พร้อมอธิบายว่าในสถานการณ์ใดข้อเสียเหล่านี้จะเด่นชัด ตัวอย่างหัวข้อที่ควรกล่าวถึง:

  - Overhead สูงสำหรับข้อมูลขนาดเล็ก (เทียบกับ DuckDB/Pandas)
  - Shuffle cost และ network I/O ในงาน wide transformation
  - ความซับซ้อนในการ tuning (memory, partitions, serialization)
  - ไม่ใช่ real-time จริง (micro-batch ใน Structured Streaming)
  - ต้นทุน infrastructure (cluster management, cloud cost)
  - Debugging ยากกว่าโปรแกรมทั่วไปเพราะ distributed nature

---

> **หมายเหตุ:** หากยกตัวอย่างเพิ่มเติมให้เขียนเป็น Python/PySpark หรือ SQL  
> หากวาดแผนภาพประกอบ ให้อธิบายส่วนประกอบให้ชัดเจน
