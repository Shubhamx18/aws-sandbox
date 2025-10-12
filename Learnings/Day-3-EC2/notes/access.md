# Accessing EC2 Instances

**Windows**
- Local: RDP using PEM key
- Console: Session Manager, EC2 Serial Console

**Linux**
- Local: SSH via PuTTY (PPK key)
- Console: EC2 Instance Connect, Session Manager, EC2 Serial Console

**Session Manager Setup**
1. Create IAM Role with `AmazonSSMManagedInstanceCore`.
2. Attach Role to EC2 instance.
3. Wait 1-2 minutes.
4. Access via RDP or Session Manager terminal.
