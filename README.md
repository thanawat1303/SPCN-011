# SPCN-011

หัวข้อที่ 1 ทำการสร้าง master vm มา 1 ตัว แล้วทำการ set ค่าพื้นฐานต่างๆ
  - set update time ด้วยคำสั่ง
    - sudo timedatectl set-timezone Asia/Bangkok
    - date
  - set qemu-guest-agent เพื่อเปิดใช้งาน ip qemu ด้วยคำสั่ง
    - sudo -i
    - apt update
    - apt install qemu-guest-agent
    - systemctl enable qemu-guest-agent
    - และทำการตั้งค่าที่ option ให้เปิดใช้งานตัว Qemu guest agent
      ![image](https://user-images.githubusercontent.com/116482588/205888715-80d93122-f42f-4585-96df-e5aa9a1e1b4e.png)
    - ทำการรีบูทระบบ
    
    เมื่อทำการ setup เสร็จแล้ว ทำการโคลนตัว vm และทำการสร้างเป็น template
    เมื่อสร้าง template แล้ว ทำการโคลนจากตัว template เป็นตัว vm สองตัว
    
    เมื่อสร้าง vm clone ขึ้นมาแล้ว
    ทำการเปิด clone ตัวแรก
      - ทำการ setup ระบบโดยการ 
        - เช็ค timezone โดยคำสั่ง date
          ![image](https://user-images.githubusercontent.com/116482588/205891789-877fa998-a5f4-45b5-8f28-5faf37569319.png)
        - เปลี่ยนค่าไอดีตัว vm เพื่อทำการขอ ip ใหม่ เพื่อไม่ให้ ip ที่เกิดจากการ โคลนจากตัว master มี ip ที่ซ้ำกัน ด้วยคำสั่ง
          - sudo -i
          - rm /var/lib/dbus/machine-id
          - nano /etc/machine-id ทำการลบตัวไอดีในไฟล์ทั้งหมด
          - ln -s /etc/machine-id /var/lib/dbus/machine-id เพื่อทำการลิ้งค์ข้อมูลตัวไฟล์ /var/lin/dbus/machine-id กับตัวไฟล์ /etc/machine-id
          - reboot
          เมื่อ reboot สำเร็จ จะได้รับการ genarate ตัวไอดีขึ้นใหม่ และได้รับ ip ใหม่เช่นกัน
          ทำขั้นตอนนี้ที่ vm clone 2 เช่นกัน

      
