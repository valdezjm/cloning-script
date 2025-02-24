🛠 Cloning with Fun! 🖥️🔄
🚀 A simple, fast, and secure disk cloning script for Linux (RHEL, Ubuntu, Debian, etc.).

This script allows you to clone an entire drive (all partitions, bootloader, and data) to multiple target drives simultaneously.

It also provides an option to securely erase target drives before cloning.

📌 Features
✅ Clone a source drive to multiple target drives at the same time
✅ Option to securely erase target drives before cloning
✅ Clones all partitions and bootloader, making the target drive bootable
✅ Uses dd for full disk cloning and sfdisk for partition table copying
✅ Displays real-time progress during cloning
✅ Safe: Allows exiting at every step to prevent mistakes

🛠 Requirements
Root or sudo access (sudo ./full_clone_tool.sh)
Linux system with dd, sfdisk, lsblk, and shred installed
Target drives must be at least as large as the source drive
📥 Installation
Download the script:
bash
git clone https://github.com/your-repo/cloning-script.git
cd cloning-script
Make the script executable:
bash
chmod +x full_clone_tool.sh
Run the script:
bash
sudo ./full_clone_tool.sh
🚀 How to Use
1️⃣ Run the script

bash
sudo ./full_clone_tool.sh
2️⃣ Select target drives

Enter one or more target drives (e.g., sdb sdc sdd)
OR type exit to quit
3️⃣ Choose to erase the target drives or skip

Secure erase (overwrites all data)
Skip if the drives are already prepared
4️⃣ Select the source drive

Enter the source drive name (e.g., sda)
OR type exit to quit
5️⃣ Confirm before cloning

Cloning starts and runs in parallel for multiple drives
Progress bars will show the copy process
6️⃣ Once cloning is done, choose to exit or clone another drive

🔹 Secure Erase Options
If you choose to erase the target drive before cloning, you get two options:

Fast Wipe (dd with zeros) – Writes all zeros to the drive, clearing partitions.
bash
Copy
Edit
dd if=/dev/zero of=/dev/sdX bs=1M status=progress

Secure Wipe (shred with 3 passes) – Overwrites with random data for security.
bash
shred -v -n 3 /dev/sdX
Use this if you are disposing of the drive.
🛑 Important Warnings
🚨 This WILL erase ALL data on the target drive(s)!
🚨 The cloned drive will be an EXACT copy of the source (including partitions & bootloader).
🚨 Only use on drives that you intend to wipe or clone!
🚨 If the source drive is encrypted, the cloned drive will also be encrypted.

🔧 Troubleshooting

❌ Problem: "Drive not found!"
✔ Fix: Make sure the drive is plugged in and visible with:
bash
lsblk -o NAME,SIZE,TYPE,MOUNTPOINT

✔ If the drive isn’t listed, try:
bash
sudo fdisk -l

❌ Problem: Cloned drive is not bootable
✔ Fix: If the source drive was bootable, the cloned drive should be as well.
✔ If the cloned drive doesn’t boot, try running:
bash
sudo grub-install --recheck /dev/sdX

📜 License
This script is free to use and modify. No warranty provided.

📞 Support
📧 Need help? Open an issue on GitHub or contact [your email/website].

📢 Happy Cloning! 🚀
Feel free to contribute improvements or report issues. 😃
