# SPCN-011

## หัวข้อที่ 1 ทำการสร้าง master vm มา 1 ตัว แล้วทำการ set ค่าพื้นฐานต่างๆ
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
   ![image](https://user-images.githubusercontent.com/116482588/207836834-2a980c74-7779-4e73-95bc-7ca7e0c4d3c7.png)
   ![image](https://user-images.githubusercontent.com/116482588/207836485-46e19271-a2d3-4145-a428-d4de177c0078.png)
   ![image](https://user-images.githubusercontent.com/116482588/207836396-d9b40cb7-2ede-43e5-9168-4e9121204487.png)

          
## หัวข้อที่ 2 สร้าง orther os 
  ใช้เป็น ubantu mint ทำการ set ค่าต่างๆ 
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
    ![image](https://user-images.githubusercontent.com/116482588/207835889-229a20da-4de6-453f-a018-4f6114fc2e00.png)
    
## หัวข้อที่ 3 ทำการสร้าง container 
  โดยจะใช้คีย์ SSH จาก Github จากการที่เรา Genarate จาก SSH Key github
  - set update time ด้วยคำสั่ง
    - sudo timedatectl set-timezone Asia/Bangkok
    - date
  ![image](https://user-images.githubusercontent.com/116482588/207841314-a5650ba0-4dbc-468f-8ba2-c125df737abc.png)



      
