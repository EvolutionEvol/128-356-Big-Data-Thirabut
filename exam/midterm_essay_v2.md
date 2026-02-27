
## ข้อสอบกลางภาค (ชุดที่ 2) — อัตนัย 4 ข้อ

> **คำชี้แจง:** ให้อธิบายอย่างครบถ้วนและชัดเจน อาจใช้ตัวอย่าง แผนภาพ หรือ pseudo-code ประกอบได้  
> แต่ละข้อ 25 คะแนน (รวม 100 คะแนน)

---

### ข้อที่ 1: วิเคราะห์สถานการณ์จริงด้วย 5Vs (25 คะแนน)

จงอ่านสถานการณ์ต่อไปนี้ แล้ววิเคราะห์ว่าปัญหาที่เกิดขึ้นสอดคล้องกับมิติใดของ **5Vs** (Volume, Velocity, Variety, Veracity, Value) พร้อมอธิบายเหตุผลอย่างละเอียด (แต่ละสถานการณ์อาจสะท้อนมากกว่า 1 มิติ)

---

**สถานการณ์ A (5 คะแนน)**

แพลตฟอร์ม e-commerce รายใหญ่จัดแคมเปญ flash sale ในช่วงเทศกาล มีผู้ใช้เข้ามาพร้อมกันกว่า 500,000 คน ภายใน 10 นาที ทำให้ระบบ recommendation engine ที่ประมวลผลแบบ batch ทุก 1 ชั่วโมงนั้นให้ผลลัพธ์ที่ไม่ทันสถานการณ์ สินค้ายอดนิยมหมดสต็อกไปแล้วแต่ระบบยังแนะนำอยู่

---

**สถานการณ์ B (5 คะแนน)**

บริษัทประกันภัยต้องการสร้าง model ประเมินความเสี่ยงของผู้เอาประกัน โดยต้องรวมข้อมูลจาก:
- ประวัติเคลม (ตาราง SQL)
- รายงานอุบัติเหตุจากตำรวจ (PDF scan)
- ภาพถ่ายความเสียหายของยานพาหนะ (image files)
- ข้อมูลจากกล่องดำในรถ (IoT telemetry แบบ time-series)

ทีมพบว่าไม่สามารถใช้ tool ตัวเดียวจัดการข้อมูลทุกรูปแบบได้

---

**สถานการณ์ C (5 คะแนน)**

มหาวิทยาลัยเก็บข้อมูลผลการเรียนจาก 3 ระบบ: ระบบลงทะเบียนเก่า (legacy), ระบบ LMS ใหม่, และ Google Classroom โดยพบว่า:
- รหัสวิชาจากแต่ละระบบไม่ตรงกัน (เช่น "CS101" vs "128-101" vs "COMP101")
- เกรดบางระบบเป็นตัวอักษร (A, B+) บางระบบเป็นตัวเลข (4.0, 3.5)
- ข้อมูลนักศึกษาจากระบบเก่ามีชื่อสะกดผิดและวันเกิดหายไปกว่า 15%
- ผลรวม GPA ที่คำนวนจากแต่ละระบบได้ค่าไม่เท่ากัน

---

**สถานการณ์ D (5 คะแนน)**

โรงงานอัจฉริยะ (smart factory) ติดตั้งเซ็นเซอร์กว่า 50,000 ตัว บนสายการผลิต แต่ละตัวส่งข้อมูลทุก 500 มิลลิวินาที ข้อมูลรวมกันกว่า 800 TB ต่อเดือน ทำให้ระบบ data warehouse เดิมที่ใช้ PostgreSQL ไม่สามารถรองรับได้ ต้องรอ query นานกว่า 2 ชั่วโมงต่อรายงาน 1 ชุด

---

**สถานการณ์ E (5 คะแนน)**

หน่วยงานรัฐเก็บข้อมูลจราจรจากกล้อง CCTV กว่า 10,000 จุดทั่วประเทศ เก็บสะสมมากว่า 5 ปี รวมกว่า 2 PB แต่ไม่เคยนำข้อมูลมาวิเคราะห์เพื่อวางแผนผังเมืองหรือลดอุบัติเหตุ จนกระทั่งมีข่าวอุบัติเหตุซ้ำซ้อนที่จุดเดิม ประชาชนตั้งคำถามว่า *"ข้อมูลที่เก็บมาทั้งหมดนำไปใช้ประโยชน์อะไรบ้าง?"*

---

### ข้อที่ 2: Columnar vs Row-based Storage — หลักการ, ข้อดี-ข้อเสีย, และการเลือกใช้ (25 คะแนน)

**คำถาม:**

**(ก)** จงอธิบายความแตกต่างระหว่าง **Columnar Storage** (เช่น Parquet) กับ **Row-based Storage** (เช่น CSV, RDBMS row store) ในเชิงโครงสร้างการจัดเก็บข้อมูล โดยอธิบายให้ครอบคลุมเรื่อง I/O pattern, compression, และ column pruning (10 คะแนน)

**(ข)** จงยกตัวอย่างสถานการณ์อย่างน้อย **3 สถานการณ์** ที่ควรเลือกใช้ Columnar Storage และ **2 สถานการณ์** ที่ Row-based Storage เหมาะสมกว่า โดยแต่ละสถานการณ์ต้องอธิบาย:
  1. ลักษณะของงาน/workload
  2. เหตุผลที่ format นั้นเหมาะสม
  3. format ที่ไม่เหมาะสมจะมีปัญหาอย่างไร (15 คะแนน)

---

### ข้อที่ 3: วิเคราะห์ Spark Code — Transformation, Action และ Execution Plan (25 คะแนน)

จงอ่าน PySpark code 3 ชุดต่อไปนี้ แล้วตอบคำถามสำหรับแต่ละชุด

---

#### Code ชุดที่ 1: วิเคราะห์ประสิทธิภาพพนักงาน

```python
from pyspark.sql import functions as F

# กำหนดตาราง: employees(emp_id, name, department, salary, hire_date, status, office_location, performance_score)

df = spark.read.parquet("s3://hr/employees/")

step1 = df.filter(F.col("status") == "active") \
          .filter(F.col("salary") > 0)

step2 = step1.withColumn("salary_band",
    F.when(F.col("salary") < 20000, "junior")
     .when(F.col("salary") < 60000, "mid")
     .otherwise("senior")
)

step3 = step2.groupBy("department", "salary_band") \
             .agg(
                 F.count("*").alias("headcount"),
                 F.avg("salary").alias("avg_salary"),
                 F.avg("performance_score").alias("avg_perf")
             )

step4 = step3.filter(F.col("headcount") >= 5) \
             .orderBy(F.col("avg_salary").desc())

step5 = step4.show(15)
```

**(1a)** จงระบุว่าแต่ละ step (step1–step5) เป็น **Transformation** หรือ **Action** พร้อมอธิบายเหตุผลสั้น ๆ (3 คะแนน)

**(1b)** Spark จะเริ่มคำนวณจริง (execute) ตรงไหน? และก่อนหน้านั้น Spark ทำอะไร? (2 คะแนน)

**(1c)** ขั้นตอนใดจะเกิด **Shuffle**? อธิบายว่าทำไมต้องย้ายข้อมูลข้าม partition (2 คะแนน)

---

#### Code ชุดที่ 2: วิเคราะห์แนวโน้มการลาออก

```python
from pyspark.sql import functions as F

# กำหนดตาราง: hr_events(event_id, emp_id, event_type, event_date, department, reason, severity)

df = spark.read.parquet("s3://hr/events/")

step1 = df.filter(F.col("event_type").isin(["resignation", "termination"])) \
          .filter(F.col("event_date") >= "2025-01-01")

step2 = step1.groupBy("department", "reason") \
             .agg(
                 F.count("*").alias("event_count"),
                 F.countDistinct("emp_id").alias("unique_employees")
             )

step3 = step2.withColumn("severity_label",
    F.when(F.col("event_count") >= 20, "critical")
     .when(F.col("event_count") >= 10, "warning")
     .otherwise("normal")
)

step4 = step3.filter(F.col("event_count") >= 3)

step5_count = step4.count()
step5_write = step4.write.mode("overwrite").parquet("s3://hr/turnover_report/")
```

**(2a)** จงระบุว่าแต่ละ step เป็น Transformation หรือ Action (3 คะแนน)

**(2b)** `step5_count` และ `step5_write` ทั้งสองเป็น Action — Spark จะรันแผนงาน (DAG) กี่ครั้ง? ทำไม? มีวิธีใดที่จะหลีกเลี่ยงการคำนวณซ้ำ? (3 คะแนน)

---

#### Code ชุดที่ 3: Pipeline จัดเตรียมข้อมูล IoT Sensor

```python
from pyspark.sql import functions as F
from pyspark.sql.types import StructType, StructField, StringType, DoubleType, TimestampType

schema = StructType([
    StructField("device_id", StringType()),
    StructField("metric_type", StringType()),
    StructField("value", DoubleType()),
    StructField("unit", StringType()),
    StructField("reading_time", TimestampType()),
    StructField("_corrupt_record", StringType())
])

raw = spark.read.csv("s3://iot/sensor_data.csv",
                     header=True, schema=schema,
                     mode="PERMISSIVE",
                     columnNameOfCorruptRecord="_corrupt_record")

step1 = raw.filter(F.col("_corrupt_record").isNull()) \
           .drop("_corrupt_record")

step2 = step1.withColumn("device_id",
    F.when(F.col("device_id").isNull(), "UNKNOWN_DEVICE")
     .otherwise(F.col("device_id"))
)

step3 = step2.withColumn("reading_date", F.to_date("reading_time")) \
             .withColumn("reading_hour", F.hour("reading_time"))

step4 = step3.filter(F.col("value").isNotNull()) \
             .filter(F.col("value") >= 0)

step5 = step4.write \
             .mode("overwrite") \
             .partitionBy("reading_date") \
             .parquet("s3://curated/sensor_data/")
```

**(3a)** จงระบุว่าแต่ละ step เป็น Transformation หรือ Action (3 คะแนน)

**(3b)** อธิบายว่าทำไม step1 ถึงกรองด้วย `_corrupt_record` เป็น null? และการ `drop("_corrupt_record")` ทำไปเพื่ออะไร? (2 คะแนน)

**(3c)** `step5` ใช้ `.write.partitionBy("reading_date").parquet(...)` — อธิบายว่าการ partition ตาม `reading_date` มีประโยชน์อย่างไรต่อการ query ในอนาคต และมี trade-off อะไรบ้าง? (2 คะแนน)

---

### ข้อที่ 4: Data Pipeline — แนวคิด, องค์ประกอบ, และความท้าทาย (25 คะแนน)

**คำถาม:**

จงอธิบาย **Data Pipeline** อย่างละเอียด โดยครอบคลุมหัวข้อต่อไปนี้:

**(ก) องค์ประกอบหลักของ Data Pipeline (15 คะแนน)** — อธิบายอย่างน้อย 5 ขั้นตอน พร้อมเหตุผลและตัวอย่าง ตัวอย่างหัวข้อที่ควรกล่าวถึง:

  - Ingestion: การนำข้อมูลเข้าจากแหล่งต่าง ๆ (batch vs streaming)
  - Validation: การตรวจสอบ schema, data type, completeness
  - Cleaning/Transformation: การจัดการ missing values, duplicates, format conversion
  - Storage: การเลือก format (Parquet, Delta) และ partitioning strategy
  - Serving/Analytics: การเตรียมข้อมูลสำหรับ dashboard, ML, หรือ reporting
  - Monitoring/Observability: การตรวจจับความผิดปกติใน pipeline

**(ข) ความท้าทายและวิธีรับมือ (10 คะแนน)** — อธิบายอย่างน้อย 4 ข้อ พร้อมอธิบายแนวทางแก้ไข ตัวอย่างที่ควรกล่าวถึง:

  - Schema evolution: เมื่อแหล่งข้อมูลเปลี่ยน schema กะทันหัน
  - Data quality: ข้อมูลที่มี null, duplicate, inconsistency
  - Scalability: เมื่อปริมาณข้อมูลเพิ่มขึ้น 10 เท่า
  - Late arriving data: ข้อมูลที่มาถึงช้ากว่ากำหนด
  - Idempotency: การ rerun pipeline แล้วได้ผลลัพธ์เหมือนเดิม
  - Cost management: การควบคุมค่าใช้จ่ายในระบบ cloud

---

> **หมายเหตุ:** หากยกตัวอย่างเพิ่มเติมให้เขียนเป็น Python/PySpark หรือ SQL  
> หากวาดแผนภาพประกอบ ให้อธิบายส่วนประกอบให้ชัดเจน
