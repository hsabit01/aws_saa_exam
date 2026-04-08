# Amazon SQS,SNS,Kinesis

# **Amazon SQS**

**Amazon SQS** is like a **digital waiting line** for messages between applications. One system drops messages into the queue, and another system picks them up later, so the two systems do not need to be available at the exact same time.

**Key Use Case:**

- Choose **SQS** when you need to **decouple applications** and handle **asynchronous processing** reliably.

**Exam Tip:**

If you see **“decouple components,” “buffer spikes,”** or **“process messages later,”** think **SQS**.

**Main Difference (SQS vs SNS):**

**SQS** = **pull-based queue** for one consumer per message.

**SNS** = **push-based pub/sub** for fan-out to many subscribers.

**Visual Logic (Mermaid):**

![amazon-sqs.png](Amazon%20SQS,SNS,Kinesis/amazon-sqs.png)

# Amazon SQS Consumer Autoscaling using SQS metrics

**SQS consumer autoscaling** means your worker fleet grows when the **queue backlog** grows and shrinks when it clears—like opening more checkout lanes when the line gets long. For **EC2 consumers**, AWS recommends scaling on **backlog per instance** using **CloudWatch metric math** and **target tracking**, instead of using raw **ApproximateNumberOfMessagesVisible** alone.

**Key Use Case:**

- Choose this when **EC2/ECS workers poll SQS** and you need to **absorb bursty workloads cost-effectively**.

**Exam Tip:**

If you see **“SQS queue backlog,” “EC2 consumers,”** or **“scale workers from queue depth,”** think **target tracking on backlog per instance**, not raw queue depth.

**Main Difference:**

**Raw queue depth** = total messages waiting.

**Backlog per instance** = messages waiting **per active consumer**, which is the better autoscaling signal.

**Visual Logic (Mermaid):**

![sqs-autoscaling.png](Amazon%20SQS,SNS,Kinesis/sqs-autoscaling.png)

# Amazon SQS Security

**Amazon SQS security** is about making sure only the **right apps** can send/receive messages, and that the messages stay **private in transit and at rest**. Think of it like a **locked mailroom**: **IAM/queue policies** decide who can enter, **encryption** protects the letters, and **VPC endpoints** keep the delivery path off the public internet.

**Key Use Case:**

- Choose these controls when you need **private, encrypted, least-privilege messaging** between AWS services or applications.

**Exam Tip:**

If you see **“encrypt SQS,” “restrict who can access the queue,”** or **“private access from VPC,”** think **SSE + IAM/queue policy + VPC endpoint**.

**Main Difference:**

**SSE-SQS** = simpler, uses **SQS-managed keys**.

**SSE-KMS** = more control, uses **AWS KMS** for tighter key policy and auditing.

**Visual Logic (Mermaid):**

![sqs-security.png](Amazon%20SQS,SNS,Kinesis/sqs-security.png)

Amazon SQS supports **identity-based policies** and **resource-based queue policies**; it supports **HTTPS**, **server-side encryption**, and **VPC endpoints/endpoint policies** for private access. 

# AWS SQS Visibility Timeout

**Visibility Timeout** is the period after a consumer receives an **SQS message** when that message is temporarily **hidden from other consumers**. Think of it like taking a job ticket off the board while you work on it—if you finish, you **delete** it; if not, it shows up again for someone else after the timer expires. The default is **30 seconds**, and you can set it as high as **12 hours**.

**Key Use Case:**

- Choose this when you want to **prevent duplicate processing while a worker is still handling a message**.

**Exam Tip:**

If you see **“message processed twice,” “long-running worker,”** or **“temporarily hide message after receive,”** think **Visibility Timeout**.

**Main Difference:**

**Visibility Timeout** hides a message **after it has been received**.

**Delay Queue** hides a message **before it is delivered the first time**.

**Visual Logic (Mermaid):**

![visibility-timeout.png](Amazon%20SQS,SNS,Kinesis/visibility-timeout.png)

# AWS SQS Long Polling

**Amazon SQS Long Polling** lets SQS **wait a little longer** for a message instead of replying immediately with “nothing there.” It is like waiting at a mailbox for a few seconds before walking away, which reduces **empty checks** and lowers cost. Long polling is enabled when **`WaitTimeSeconds` > 0**, up to **20 seconds**.

**Key Use Case:**

- Choose **Long Polling** when consumers check SQS often and you want to **reduce empty responses, API calls, and cost**.

**Exam Tip:**

If you see **“too many empty receives,” “reduce polling cost,”** or **“wait for messages to arrive,”** think **SQS Long Polling**.

**Main Difference:**

**Short polling** = checks quickly and may return **empty / false empty** responses.

**Long polling** = waits up to **20 seconds** and queries more broadly, so it reduces **empty** and **false empty** responses.

**Visual Logic (Mermaid):**

![sqs-long-polling.png](Amazon%20SQS,SNS,Kinesis/sqs-long-polling.png)

# AWS SQS FIFO

**Amazon SQS FIFO** is a queue type for messages that must be handled in the **exact order** they were sent, while also helping prevent **duplicate messages**. Think of it like people standing in a **single-file line** where nobody can cut, and the same ticket is not handed out twice. FIFO queues preserve order **within a message group** and use **deduplication IDs** or **content-based deduplication** to avoid duplicates.

**Key Use Case:**

- Choose **SQS FIFO** when your workload needs **strict ordering** and **deduplication**, such as financial transactions, ordered commands, or sequential updates.

**Exam Tip:**

If you see **“strict order,” “no duplicates,”** or **“same sequence must be preserved,”** think **SQS FIFO**. If you see **“maximum throughput matters more than ordering,”** think **Standard SQS** instead. FIFO queues have lower default throughput than Standard queues, though AWS supports **high-throughput mode** for FIFO.

**Main Difference:**

**Standard SQS** = best effort ordering, **at-least-once** delivery.

**FIFO SQS** = **ordered processing** and **deduplication/exactly-once processing behavior**.

**Visual Logic (Mermaid):**

![sqs-fifo.png](Amazon%20SQS,SNS,Kinesis/sqs-fifo.png)

# Amazon SNS

**Amazon SNS** is a **push-based messaging service** that sends one message to **many subscribers** at the same time. Think of it like a **group announcement system**: you post once to a topic, and SNS fans it out to **SQS queues, Lambda, HTTP/S endpoints, email, or mobile push** subscribers.

**Key Use Case:**

- Choose **SNS** when you need **fan-out pub/sub** so multiple systems react to the same event in parallel.

**Exam Tip:**

If you see **“fan out to multiple targets,” “publish/subscribe,”** or **“push notifications,”** think **SNS**.

**Main Difference:**

**SNS** = **push** to many subscribers.

**SQS** = **pull** from a queue, usually for buffering and decoupling.

For strict ordering and deduplication, **SNS FIFO** can work with **SQS FIFO**.

**Visual Logic (Mermaid):**

![amazon-sns.png](Amazon%20SQS,SNS,Kinesis/amazon-sns.png)

# Amazon SNS Security

**Amazon SNS security** is about making sure only the **right publishers and subscribers** can use a topic, and that messages stay **protected in transit and at rest**. Think of it like a **secure broadcast station**: **IAM/topic policies** decide who can speak or listen, **KMS encryption** protects the message, and **VPC endpoints** keep traffic off the public internet.

**Key Use Case:**

- Choose these controls when you need **encrypted, least-privilege, private pub/sub messaging** across AWS services or applications.

**Exam Tip:**

If you see **“secure SNS topic,” “encrypt notifications,” “restrict publish/subscribe,”** or **“private access from VPC,”** think **KMS encryption + IAM/topic policy + VPC endpoint**.

**Main Difference:**

**IAM policies** control what an identity can do.

**SNS topic policies** control who can access the **topic resource** itself, including cross-account access. Also, **SNS uses SSE with AWS KMS** for topic encryption; unlike SQS, there is no SNS-managed SSE option comparable to **SSE-SQS**.

**Visual Logic (Mermaid):**

![sns-security.png](Amazon%20SQS,SNS,Kinesis/sns-security.png)

# Amazon SNS + SQS Fan out

**SNS + SQS fan-out** means you publish **one message** to an **SNS topic**, and SNS automatically copies it to **multiple SQS queues**. Think of it like making **one announcement over a loudspeaker**, while each team gets its **own inbox** to process the same event independently and at its own pace.

**Key Use Case:**

- Choose this when **multiple systems** need to react to the **same event** with **parallel, decoupled processing**.

**Exam Tip:**

If you see **“one message to many applications,” “multiple subscribers,”** or **“fan-out event to separate queues,”** think **SNS topic → multiple SQS queues**.

**Main Difference:**

**SNS alone** = pushes notifications directly to subscribers.

**SNS + SQS fan-out** = each subscriber gets its **own queue**, so services are more **durable, decoupled, and retry-friendly**.

**Visual Logic (Mermaid):**

![sns-sqs-fanout.png](Amazon%20SQS,SNS,Kinesis/sns-sqs-fanout.png)

# Amazon Kinesis Data Stream

**Amazon Kinesis Data Streams** is like a **live conveyor belt** for data: producers keep dropping in events, and consumers read them in near real time. It is built for **streaming data ingestion and processing**, stores data in **shards**, and lets you **replay** records during the retention period, which is **24 hours by default** and can be extended up to **365 days**.

**Key Use Case:**

- Choose **Kinesis Data Streams** when you need **real-time streaming**, **multiple consumers**, and the ability to **replay data** later.

**Exam Tip:**

If you see **“real-time stream of logs/clickstreams/events,” “multiple consumers,”** or **“replay streaming data,”** think **Kinesis Data Streams**. If AWS wants fully managed delivery **to destinations** with less custom consumer logic, think **Kinesis Data Firehose** instead.

**Main Difference:**

**Kinesis Data Streams** = build your own consumers and keep data for replay.

**SQS** = message queue for decoupling; **Kinesis** is for **ordered streaming data** across shards and real-time analytics patterns.

**Visual Logic (Mermaid):**

![kinesis.png](Amazon%20SQS,SNS,Kinesis/kinesis.png)

# Amazon Data Firehose

**Amazon Data Firehose** is a **fully managed delivery service** for streaming data into destinations like **Amazon S3, Redshift, OpenSearch Service, Splunk, and HTTP endpoints**. Think of it like a **smart conveyor belt**: data comes in continuously, Firehose can **buffer, transform, and compress** it, then automatically drops it into the right destination. It was previously called **Kinesis Data Firehose**.

**Key Use Case:**

- Choose **Amazon Data Firehose** when you want to **ingest streaming data and deliver it automatically** to storage/analytics destinations **without managing consumers**.

**Exam Tip:**

If you see **“load streaming data into S3/Redshift/OpenSearch,” “fully managed delivery,”** or **“no custom consumer code,”** think **Amazon Data Firehose**.

**Main Difference:**

**Kinesis Data Streams** = you build/read with your own consumers.

**Amazon Data Firehose** = AWS **automatically delivers** the stream to destinations for you.

**Visual Logic (Mermaid):**

![amazon-firehose.png](Amazon%20SQS,SNS,Kinesis/amazon-firehose.png)

# Amazon Data Firehose vs Amazon Kinesis Data Stream

**Amazon Kinesis Data Streams** is like a **live event conveyor belt** that applications can read from in near real time, and even **replay later** during the retention window. **Amazon Data Firehose** is more like a **managed delivery truck**: it takes streaming data, can **buffer/transform/compress** it, and automatically delivers it to places like **S3, Redshift, OpenSearch, and HTTP endpoints**.

**Key Use Case:**

- Choose **Kinesis Data Streams** when you need **custom real-time consumers, multiple readers, and replay**; choose **Amazon Data Firehose** when you want **fully managed delivery to destinations** with minimal operational work.

**Exam Tip:**

If you see **“real-time stream + custom consumers + replay,”** think **Kinesis Data Streams**. If you see **“deliver streaming data to S3/Redshift/OpenSearch with minimal management,”** think **Amazon Data Firehose**.

**Main Difference:**

**Kinesis Data Streams** = **you manage/read the stream**.

**Amazon Data Firehose** = **AWS delivers the stream for you**. Also, AWS now calls it **Amazon Data Firehose**; it was previously **Kinesis Data Firehose**.

**Visual Logic (Mermaid):**

![amazon-firehose-vs-kinesis.png](Amazon%20SQS,SNS,Kinesis/amazon-firehose-vs-kinesis.png)

# SQS vs SNS vs Kinesis

**SQS** is a **digital waiting line**: producers drop in messages, and consumers **pull** them later for decoupled processing. **SNS** is a **loudspeaker**: one message is **pushed** to many subscribers at once. **Kinesis Data Streams** is a **live conveyor belt** for high-volume event data that multiple consumers can process in near real time and **replay** during the retention window.

**Key Use Case:**

- Choose **SQS** for **buffering/decoupling**, **SNS** for **fan-out notifications**, and **Kinesis Data Streams** for **real-time streaming analytics or replayable event streams**.

**Exam Tip:**

If you see **“queue and process later”**, think **SQS**; **“one event to many subscribers”**, think **SNS**; **“real-time stream with replay/multiple consumers”**, think **Kinesis Data Streams**.

**Main Difference:**

**SQS** = **pull-based queue** for decoupling. **SNS** = **push-based pub/sub** for fan-out. **Kinesis Data Streams** = **streaming platform** for ordered data records across a stream, with consumer apps reading the stream and replaying data during retention.

**Visual Logic (Mermaid):**

![sqs-sns-kinesis.png](Amazon%20SQS,SNS,Kinesis/sqs-sns-kinesis.png)

# Amazon MQ

**Amazon MQ** is a **managed message broker** for **Apache ActiveMQ Classic** and **RabbitMQ**. Think of it like AWS running the **mailroom server** for you, so apps that already speak traditional messaging protocols can keep working **without a big rewrite**.

**Key Use Case:**

- Choose **Amazon MQ** when you need **ActiveMQ/RabbitMQ compatibility** or want to **migrate existing broker-based apps** to AWS with minimal code changes.

**Exam Tip:**

If you see **“migrate existing messaging app,” “JMS/AMQP/MQTT/STOMP/OpenWire,”** or **“don’t rewrite the application,”** think **Amazon MQ**.

**Main Difference:**

**Amazon MQ** = **managed broker** for existing messaging protocols.

**SQS/SNS** = **cloud-native AWS messaging services** that usually fit new AWS-native designs better.

**Visual Logic (Mermaid):**

![amazon-mq.png](Amazon%20SQS,SNS,Kinesis/amazon-mq.png)