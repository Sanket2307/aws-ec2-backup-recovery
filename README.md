# aws-ec2-backup-recovery
EC2 Backup and Disaster Recovery using EBS Snapshots on AWS

## Project Overview
This project demonstrates the implementation of a **backup and disaster recovery solution** for an AWS EC2 instance using **EBS snapshots**.  
The objective is to protect application data, simulate real storage failure, and successfully restore data from backups, following industry best practices.

The project includes:
- EC2 instance setup
- Separate EBS data volume
- Manual snapshot-based backup
- Real disaster simulation
- Data recovery validation

---

## Architecture Explanation
The architecture consists of:
- An EC2 instance running Amazon Linux
- A separate EBS data volume mounted at `/data`
- EBS snapshots used as the backup mechanism
- Volume recreation from snapshot for recovery

**Flow:**
1. Application data is stored on a dedicated EBS data volume
2. Snapshots are created from the data volume
3. In case of failure, the volume is deleted
4. A new volume is created from the snapshot and reattached
5. Data integrity is verified after recovery

---

## Backup Process
1. Launch an EC2 instance and attach a separate EBS data volume
2. Format and mount the volume at `/data`
3. Store application and log files on the data volume
4. Create a **manual EBS snapshot** of the data volume
5. Verify snapshot completion before proceeding

This snapshot acts as a **point-in-time backup** of the data.

---

## Recovery Test (Disaster Simulation)
To validate recovery:
1. Stop the EC2 instance
2. Detach and delete the EBS data volume (simulate disk failure)
3. Create a new volume from the snapshot
4. Attach the restored volume to the EC2 instance
5. Start the instance and mount the volume
6. Verify that all original files are restored correctly

This confirms that the backup is **usable and reliable**.

---

## RPO and RTO
- **Recovery Point Objective (RPO):** 24 hours  
  (Based on daily snapshot frequency)

- **Recovery Time Objective (RTO):** 10–15 minutes  
  (Time required to recreate and attach volume, and mount it)

---

## Screenshots
The following screenshots are included to validate each stage:
- EC2 instance running
- SSH connection to instance
- EBS volume attached
- Data created inside `/data`
- Snapshot creation and completion
- Volume deletion (failure simulation)
- Volume restored from snapshot
- Data successfully recovered

All screenshots are stored in the `screenshots/` directory.

---

## Key Learnings
- Difference between **backup** and **recovery**
- Importance of separating root and data volumes
- Practical use of EBS snapshots
- Handling NVMe device naming on Nitro-based instances
- Real-world disaster recovery testing
- Cost-effective backup strategy on AWS

---

## Conclusion
This project demonstrates a complete **end-to-end backup and recovery workflow** on AWS using EC2 and EBS snapshots.  
It follows real-world practices and validates recovery through actual failure simulation, making it suitable for academic, internship, and entry-level cloud roles.
