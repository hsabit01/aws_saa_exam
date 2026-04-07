# AWS Storage Extras

# AWS Snowball

**AWS Snowball** is like ordering a **secure hard-drive appliance from AWS**, loading your huge amount of data onto it in your data center, and then shipping it back to AWS instead of sending everything over a slow internet connection. It’s part of the **AWS Snow Family** and is designed for moving **terabytes to petabytes** of data when network transfer would take too long.

**Key Use Case:**

- Choose **Snowball** when you need to migrate **very large datasets** to AWS and your available bandwidth is limited or unreliable.

**Exam Tip:**

**If you see “petabytes of data,” “limited bandwidth,” or “remote/disconnected site,” think *Snowball*.**

**Main Difference (similar services):**

**Snowball vs DataSync:** **Snowball** = **physical/offline transfer device**; **DataSync** = **online network-based transfer**. AWS now notes that **Snowball Edge is no longer available to new customers**, but Snowball remains the classic exam answer for massive offline migrations.

**Visual Logic (Mermaid):**

![aws-snowball.png](AWS%20Storage%20Extras/aws-snowball.png)

# AWS Edge Computing

**AWS Edge Computing** means running compute or storage **closer to where users or devices are**, instead of always sending everything back to a distant AWS Region. Think of it like putting a **mini service counter near customers** so they get faster service; in AWS, this can mean services like **Local Zones**, **Wavelength**, **Outposts**, or other edge options depending on the latency need.

**Key Use Case:**

- Choose **AWS Edge Computing** when you need **very low latency**, **local processing**, or to keep apps/data **closer to users, devices, or on-prem sites**.

**Exam Tip:**

**If you see “ultra-low latency,” “close to users,” “5G/mobile edge,” or “on-prem but AWS-managed,” think *Edge Computing*** — then narrow it to **Local Zones**, **Wavelength**, or **Outposts**.

**Main Difference (similar services):**

**Local Zones** = closer to **city/end users**; **Wavelength** = closer to **5G mobile users via telecom carriers**; **Outposts** = AWS infrastructure installed **in your own data center/site**.

![aws-edge-computing.png](AWS%20Storage%20Extras/aws-edge-computing.png)

# Snowball into Glacier

Think of **AWS Snowball into Glacier** like using a **secure shipping container** to move a giant archive to AWS, then putting it into a **low-cost long-term storage vault** afterward. In practice, **Snowball imports data into Amazon S3 first**, and then you typically use an **S3 Lifecycle rule** to transition it to **S3 Glacier Flexible Retrieval** or **S3 Glacier Deep Archive**.

**Key Use Case:**

- Choose this when you need to move **massive archival datasets** to AWS and your network is too slow for online transfer.

**Exam Tip:**

**If you see “petabytes + archive + limited bandwidth,” think *Snowball to S3, then Lifecycle to Glacier* — not direct upload to Glacier.**

**Main Difference (similar services):**

**Snowball vs Glacier:** **Snowball** = **how you move huge data physically**; **Glacier** = **where you store archive data cheaply for the long term**.

**Visual Logic (Mermaid):**

![snowball-into-glacier.png](AWS%20Storage%20Extras/snowball-into-glacier.png)

# Amazon FSx

**Amazon FSx** is AWS’s **fully managed file storage** service for when you need a **real file system**, not just object storage like S3. Think of it like renting a **specialized shared network drive** from AWS, where you choose the version that best fits your workload: **Windows**, **Lustre**, **NetApp ONTAP**, or **OpenZFS**.

**Key Use Case:**

- Choose **Amazon FSx** when your application needs **shared file storage** with a specific file system type, such as **Windows file shares**, **high-performance HPC/ML storage**, or **enterprise NAS features**.

**Exam Tip:**

**If you see “managed file system” or “shared file storage,” think *FSx* — then map the workload: Windows = FSx for Windows, HPC/ML = FSx for Lustre.**

**Main Difference (similar services):**

**FSx vs EFS:** **FSx** = choose a **specific file system** for specialized workloads; **EFS** = simple **serverless NFS** for general Linux shared storage.

**Inside FSx:** **Windows** = SMB/Windows apps, **Lustre** = HPC/ML + S3 integration, **ONTAP/OpenZFS** = advanced NAS features.

**Visual Logic (Mermaid):**

![aws-fsx.png](AWS%20Storage%20Extras/aws-fsx.png)

# AWS Storage Gateway

**AWS Storage Gateway** is like a **bridge between your on-prem data center and AWS storage**. It lets your existing servers keep using familiar **file, block, or tape-style storage**, while the actual data can be backed by AWS storage services like **Amazon S3** and archive tiers.

**Key Use Case:**

- Choose **Storage Gateway** when a company wants a **hybrid storage** setup: keep on-prem apps, but extend backup, archive, or shared storage into AWS.

**Exam Tip:**

**If you see “on-premises application needs seamless access to AWS storage,” think *Storage Gateway*.** For subtypes: **File = NFS/SMB to S3**, **Volume = iSCSI block**, **Tape = virtual tape backup to AWS**.

**Main Difference (similar services):**

**Storage Gateway vs DataSync:** **Storage Gateway** = ongoing **hybrid access/integration**; **DataSync** = **data transfer/migration** job.

Inside Storage Gateway: **File Gateway** = file shares, **Volume Gateway** = block storage, **Tape Gateway** = backup/archive replacement for physical tapes.

**Visual Logic (Mermaid):**

![aws-storage-gateway.png](AWS%20Storage%20Extras/aws-storage-gateway.png)

# AWS File Gateway

**AWS File Gateway** is a type of **AWS Storage Gateway** that lets your on-prem servers use familiar **NFS or SMB file shares**, while the files are actually stored as **objects in Amazon S3**. Think of it like putting a **local office file cabinet in front of a giant cloud warehouse**: users work with normal files, and File Gateway handles the sync plus **local caching** for faster access.

**Key Use Case:**

- Choose **File Gateway** when you want **on-prem apps to access AWS storage through file protocols** without rewriting them for S3 APIs.

**Exam Tip:**

**If you see “NFS/SMB access to S3,” “hybrid file storage,” or “local cache with cloud-backed files,” think *AWS File Gateway*.**

**Main Difference (similar services):**

**File Gateway vs Storage Gateway:** **File Gateway** is the **file-share** option inside **Storage Gateway**.

**File Gateway vs DataSync:** **File Gateway** = ongoing **hybrid file access**; **DataSync** = **transfer/migration** service.

**Visual Logic (Mermaid):**

![aws-file-gateway.png](AWS%20Storage%20Extras/aws-file-gateway.png)

# AWS Volume Gateway

**AWS Volume Gateway** is a type of **AWS Storage Gateway** that gives your on-prem servers **block storage volumes** over **iSCSI**, while the data is backed by **Amazon S3**. Think of it like giving your local application a **virtual hard drive**, but most of the storage actually lives in AWS, with local access for speed where needed.

**Key Use Case:**

- Choose **Volume Gateway** when an **on-prem application needs block storage** but you want to use AWS for **durability, backup, and scalable backend storage**.

**Exam Tip:**

**If you see “iSCSI block storage from on-prem to AWS,” think *Volume Gateway*.**

Extra trigger: **Cached volumes** = most data in AWS with hot data cached locally.

**Main Difference (similar services):**

**Volume Gateway vs File Gateway:** **Volume Gateway** = **block storage (iSCSI)**; **File Gateway** = **file storage (NFS/SMB) to S3**.

Within Volume Gateway, **Cached volumes** keep primary data in **S3** and only frequently accessed data locally.

**Visual Logic (Mermaid):**

![aws-volume-gateway.png](AWS%20Storage%20Extras/aws-volume-gateway.png)

# AWS Tape Gateway

**AWS Tape Gateway** is a type of **AWS Storage Gateway** that replaces **physical backup tapes** with **virtual tapes in AWS**. Think of it like keeping your old tape backup process, but swapping the fragile tape cartridges for a **cloud-based tape library** that stores data in **Amazon S3** and archives it to **S3 Glacier** tiers.

**Key Use Case:**

- Choose **Tape Gateway** when a company wants to **modernize tape-based backup and archive workflows** without changing its existing backup software.

**Exam Tip:**

**If you see “replace physical tapes,” “virtual tape library (VTL),” or “existing backup software with cloud archive,” think *Tape Gateway*.**

**Main Difference (similar services):**

**Tape Gateway** = **virtual tapes for backup/archive workflows**; **File Gateway** = **file shares to S3**; **Volume Gateway** = **iSCSI block storage**.

**Visual Logic (Mermaid):**

![aws-tape-gateway.png](AWS%20Storage%20Extras/aws-tape-gateway.png)

# AWS Transfer Family

**AWS Transfer Family** is a managed way to let people and partner systems send files into AWS using familiar protocols like **SFTP, FTPS, FTP, and AS2**, without rebuilding everything around S3 APIs. Think of it like putting a **front desk** in front of **Amazon S3 or EFS** so outside systems can keep using the file-transfer methods they already know.

**Key Use Case:**

- Choose **AWS Transfer Family** when you need to **migrate or run B2B/file-transfer workflows into AWS** while keeping existing client tools and protocols.

**Exam Tip:**

**If you see “SFTP/FTPS/FTP/AS2 into S3 or EFS,” think *AWS Transfer Family*.**

**Main Difference (similar services):**

**Transfer Family vs DataSync:** **Transfer Family** = managed **file transfer endpoints/protocols for users and partners**; **DataSync** = managed **bulk data movement/sync** between storage systems.

Also, **Transfer Family** lands data in **S3 or EFS**.

**Visual Logic (Mermaid):**

![aws-transfer-family.png](AWS%20Storage%20Extras/aws-transfer-family.png)

# AWS DataSync

**AWS DataSync** is a managed service for moving data **online** between **on-premises storage, other clouds, and AWS storage**. Think of it like a **smart moving company** for files and objects: it handles copying, scheduling, validation, and moving only what changed instead of making you do it manually.

**Key Use Case:**

- Choose **DataSync** when you need to **migrate or sync large datasets over the network** into **S3, EFS, FSx, or between storage locations** on a recurring or one-time basis.

**Exam Tip:**

**If you see “online transfer,” “scheduled sync,” “incremental copy,” or “move data between on-prem and AWS storage,” think *DataSync*.**

**Main Difference (similar services):**

**DataSync vs Snowball:** **DataSync** = **online network transfer**; **Snowball** = **offline physical device** for huge transfers when bandwidth is poor. Also, DataSync can move data directly to archive classes such as **S3 Glacier** storage classes for cold data workflows.

**Visual Logic (Mermaid):**

![aws-data-sync.png](AWS%20Storage%20Extras/aws-data-sync.png)