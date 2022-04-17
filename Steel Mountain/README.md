                                                         Steel Mountain- TryHackMe CTF


![Mr _Robot_Logo](https://user-images.githubusercontent.com/97130195/163723497-74ab9a93-14a2-43f2-9bf0-4c0230d82dd7.svg)

TASK 1: INTRODUCTION




<img width="567" alt="IMAGE!1" src="https://user-images.githubusercontent.com/97130195/163723656-e1fc976d-a739-4508-bcfb-2e6d79824b4d.png">
A few ways to do this. Now what I did was I went into my Kali machine and opened my Firefox browser. Once the browser is open in the URL bar type: HTTP://targetmachineIP
(I recommend leaving this browser open for our next task)





You are then met with this page:






<img width="599" alt="SteelmountainImage1" src="https://user-images.githubusercontent.com/97130195/163723972-f8537a72-c871-40cd-85fa-2204c3354f13.png">
From this point you can right click on the image. Inspect element and it reveals...


![Screenshot 2022-04-17 114356](https://user-images.githubusercontent.com/97130195/163724327-321aab2a-8c88-44ac-830b-18c3912dc722.png)

Answer: Bill Harper

TASK 2: INITIAL ACCESS

<img width="577" alt="nextimage1" src="https://user-images.githubusercontent.com/97130195/163724614-1065a4fe-526e-4c50-a875-a1e16fde7ffc.png">
Open a terminal on your machine and run this NMAP command:
nmap -sV (targetmachineIP)
This should return something along the lines of this:
<img width="574" alt="SteelmountainImage4" src="https://user-images.githubusercontent.com/97130195/163724841-1eaecf47-340c-40d2-9022-92da246200d2.png">
From here we can see the open port and the service running(this will be our next question)


Answer: 8080

<img width="577" alt="SteelmountainImage12" src="https://user-images.githubusercontent.com/97130195/163724938-8ddcdb5d-bd93-428b-94c5-22d140845338.png">
If we go back to our Browser screen and since we know the port that is open is 8080 let's type this in...

![Screenshot 2022-04-17 121026](https://user-images.githubusercontent.com/97130195/163725136-eed0f13a-612f-4a98-8715-9b55956a7321.png)
Now lets click on the hyper link provided in the bottom left corner to get our next answer

![Screenshot 2022-04-17 121225](https://user-images.githubusercontent.com/97130195/163725188-4747171f-476e-4ef1-b9d3-83d4abd06dc4.png)

Answer: Rejetto HTTP File Server

Next lets find an exploit on exploit DB

<img width="330" alt="SteelmountainImage12" src="https://user-images.githubusercontent.com/97130195/163725331-518aa756-fda2-4edb-b95e-a52972076602.png">


<img width="564" alt="SteelmountainImage7" src="https://user-images.githubusercontent.com/97130195/163725286-3ae60ea0-52f0-44be-854e-c0ec7a9c944a.png">

Answer: 2014-6287

<img width="344" alt="SteelmountainImage12" src="https://user-images.githubusercontent.com/97130195/163725413-3b45fbca-2347-41e8-a6b9-8198ebea3010.png">

First thing we are going to do is launch Metasploit with the command msfconsole and then follow along for the steps on the screenshots below

<img width="581" alt="SteelmountainImage8 2" src="https://user-images.githubusercontent.com/97130195/163725564-d9d4fd59-cc84-42be-b047-881f93750c86.png">
<img width="587" alt="SteelmountainImage9" src="https://user-images.githubusercontent.com/97130195/163725612-7db8455a-e060-48bf-90ae-a7d45f5c7977.png">
<img width="579" alt="SteelmountainImage10" src="https://user-images.githubusercontent.com/97130195/163725630-93a73e18-580d-44ae-aea7-563c22fd9fe6.png">
Now for out answer...
<img width="578" alt="SteelmountainImage11" src="https://user-images.githubusercontent.com/97130195/163725668-9bcdab56-715f-4ae7-8098-7a92c9e0d29b.png">

Answer: b04763b6fcf51fcd7c13abc7db4fd365

TASK 3: PRIVILEGE ESCALATION


![Screenshot 2022-04-17 123050](https://user-images.githubusercontent.com/97130195/163725845-c29dcc0e-792c-436b-b204-21e26eee2537.png)



Using our established connection. Either background this or in a new tab.
<img width="589" alt="SteelmountainImage13" src="https://user-images.githubusercontent.com/97130195/163725976-2c51cdbe-f6eb-4123-858b-dcfe62740dea.png">

Then upload this


<img width="571" alt="SteelmountainImage15" src="https://user-images.githubusercontent.com/97130195/163726049-ae6ad939-f4d4-4558-9e51-3a80c986cb2d.png">

Answer: Not Needed

![Screenshot 2022-04-17 123349](https://user-images.githubusercontent.com/97130195/163725891-92ac878b-8eac-4b64-add9-06a76471588c.png)
<img width="581" alt="SteelMountain18" src="https://user-images.githubusercontent.com/97130195/163726293-70511dce-ee51-48d0-8c49-421442ff7d5a.png">


Answer: AdvancedSystemCareService9
![Screenshot 2022-04-17 124542](https://user-images.githubusercontent.com/97130195/163726248-3999b0f2-cf98-4f1f-9490-0a1f5bfef136.png)

Edit the above msvenom command to your IPs and then run it.
<img width="572" alt="Screenshot 2022-04-10 174112" src="https://user-images.githubusercontent.com/97130195/163726655-490bfdaf-349a-4bf6-9e76-5e4f9ac9382e.png">

![Screenshot 2022-04-17 131349](https://user-images.githubusercontent.com/97130195/163727172-1b652634-9d86-4f78-af48-ce8b27495977.png)


Follow these commands

<img width="539" alt="Screenshot 2022-04-10 163459" src="https://user-images.githubusercontent.com/97130195/163726515-fc4933f4-8c4a-4474-8452-696c2fa477ff.png">
<img width="546" alt="Screenshot 2022-04-10 163349" src="https://user-images.githubusercontent.com/97130195/163726536-b224e21a-905b-4954-a2bf-0397ca3fb477.png">

Start a listener using ports in msfvenom command: nc -nlvp 4443(your LPORT)


<img width="446" alt="Screenshot 2022-04-10 222244" src="https://user-images.githubusercontent.com/97130195/163727034-e5781162-f605-4691-80ea-eaed78dd0d10.png">

<img width="562" alt="Screenshot 2022-04-10 180156" src="https://user-images.githubusercontent.com/97130195/163726922-aec05fd3-d838-4ab6-955d-10d11d5df822.png">

<img width="584" alt="Screenshot 2022-04-10 221305" src="https://user-images.githubusercontent.com/97130195/163726822-8189cae7-c3e7-445d-895b-000098e78bfb.png">
<img width="524" alt="Screenshot 2022-04-10 222214" src="https://user-images.githubusercontent.com/97130195/163726828-db559dd2-2b41-49c8-b423-13ceec83bfd2.png">
<img width="562" alt="Screenshot 2022-04-10 180156" src="https://user-images.githubusercontent.com/97130195/163726970-b6a1a912-56f9-457e-94f8-3b0b283d5e76.png">
<img width="369" alt="Screenshot 2022-04-10 222600" src="https://user-images.githubusercontent.com/97130195/163727091-a22d5e18-02c2-4b56-a0d3-a20272de2bac.png">
<img width="350" alt="Screenshot 2022-04-10 222743" src="https://user-images.githubusercontent.com/97130195/163727102-7c1166cd-b109-484c-a186-b751d50c47eb.png">
<img width="352" alt="Screenshot 2022-04-10 222914" src="https://user-images.githubusercontent.com/97130195/163727113-ef92536f-04ab-4872-81ab-8b19cea5aa04.png">
Answer: 9af5f314f57607c00fd09803a587db80

TASK 4:  Access and Escalation Without Metasploit

![Screenshot 2022-04-17 131619](https://user-images.githubusercontent.com/97130195/163727293-e6acc9a5-4c0f-47f8-909a-3169604d360a.png)
This one is a little tricky if you are using the attack box as most THM attack boxes already have port 80 already taken, so with the exploit script I suggest changing this port.
![task4](https://user-images.githubusercontent.com/97130195/163727350-2b714302-ae05-4788-b28e-975024ad4554.png)
For this be sure to use a text editor and edit the LHOST and LPORT in the exploit script.
![task4 2](https://user-images.githubusercontent.com/97130195/163727355-bb532be8-b49a-47ca-a653-f79cbbf980fb.png)


![task4 3](https://user-images.githubusercontent.com/97130195/163727357-757e1c5b-a570-4114-bb01-f2f795baf120.png)
![task4 4](https://user-images.githubusercontent.com/97130195/163727365-1272d661-8e4c-4a4a-a036-116c547e7daf.png)
![task4 5](https://user-images.githubusercontent.com/97130195/163727371-c3fb1b0c-af32-4d48-b581-6cb4451c9775.png)
![task4 6](https://user-images.githubusercontent.com/97130195/163727374-74a9f504-4e9d-4685-b18e-d4abd0b3d8a5.png)
![task4 7](https://user-images.githubusercontent.com/97130195/163727379-d38112d6-29c7-4185-8059-690050c21f93.png)
![task4 8](https://user-images.githubusercontent.com/97130195/163727382-4c6afd10-8a74-408b-ae41-dc93b7fd1c93.png)
![task4 9](https://user-images.githubusercontent.com/97130195/163727390-0d50c41f-9163-4e65-a928-7f86a9f47285.png)

Answer: Not needed

![Screenshot 2022-04-17 133122](https://user-images.githubusercontent.com/97130195/163727821-b6690cf0-14a8-4f64-8743-32c8057f5548.png)
![Screenshot 2022-04-16 203314](https://user-images.githubusercontent.com/97130195/163727914-24ea60cc-c1c7-4973-9c9b-507f5af84451.png)


![Screenshot 2022-04-16 203404](https://user-images.githubusercontent.com/97130195/163727584-5bc52323-f554-46d4-8fc7-a2c2095219dc.png)
![Screenshot 2022-04-16 204314](https://user-images.githubusercontent.com/97130195/163727588-3a7697cd-6613-4e6c-8d63-8e78c9195f18.png)
