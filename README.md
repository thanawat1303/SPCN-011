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
   
   summary
    
    master : ![image](https://user-images.githubusercontent.com/116482588/208134714-f1057616-b8ca-479b-8e53-7e2e35c15897.png)
    clone 1 : ![image](https://user-images.githubusercontent.com/116482588/208135693-d3b86681-268e-4d6d-9826-2a1de48780ce.png)
    clone 2 : ![image](https://user-images.githubusercontent.com/116482588/208135949-acc2956d-ecde-4aff-bf36-7a04c9e17636.png)
   
   watch
    
    clone 1 :
      ![image](https://user-images.githubusercontent.com/116482588/208139605-5a9e7554-7032-47bd-907e-81a88fa7c282.png)
    clone 2 :
      ![image](https://user-images.githubusercontent.com/116482588/208140725-8e718e08-7170-42e4-bac1-5229f5f5ddb5.png)
          
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
    ![image](https://user-images.githubusercontent.com/116482588/208141316-d2a7d9e9-e26c-43a7-915b-e01b6142bbe3.png)
    
## หัวข้อที่ 3 ทำการสร้าง container 
  โดยจะใช้คีย์ SSH จาก Github จากการที่เรา Genarate จาก SSH Key github
  - set update time ด้วยคำสั่ง
    - sudo timedatectl set-timezone Asia/Bangkok
    - date
  
  summary 
    
    ![image](https://user-images.githubusercontent.com/116482588/208141432-f3725531-bc17-418d-8b92-f59102b1b070.png)
  
  console
    
    ![image](https://user-images.githubusercontent.com/116482588/208141547-0fa77d12-c4ff-412c-98a2-750ece39c714.png)




      
