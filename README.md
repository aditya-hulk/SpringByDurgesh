# 1. Spring Framework Course Overview.
![alt text](image.png)![alt text](image-1.png)
### Web related terms such as Html,Css,Js bootstraps etc.
![alt text](image-2.png)![alt text](image-3.png)
# 2. What is Spring Framework | Dependency Injection | Inversion of Control | Spring Core Module
![alt text](image-4.png)![alt text](image-5.png)![alt text](image-6.png)
- Kal Geeta ke jagah yadi bablu ka object ki requirement hue Ram ko
    - So pure code mein jaha jaha Geeta ka object hai wo replace karna honga bablu ke object se.
- So basically every time we have to change code and compile it again.

![alt text](image-7.png)
- kal yadi Geeta ka jaagah bablu ka object chaiye ramu ko
    - to Spring uska bhi object create karke de denga.
    - isme aapko code ko bar bar compile nhi karna padenga.

![alt text](image-8.png)![alt text](image-9.png)![alt text](image-10.png)
# 3. Overview of Spring Framework module.
![alt text](image-11.png)
### Spring Core:
- Consist of 4 module namely Core, beans, context,spel.
- Core & beans provide basic thing like dependency injection and IOC.
    - iske wajah se hi hum dependency inject kar sakte 
    - constructor/ setter injection all stuff.
- Context provide event propagation,resource loading, transperent creation of context, internationalization.
- Spel  abbreviate as expression language 
    - With this we can query or manipulate object graph at runtime.
### AOP
- Consist of 3 module namely Aspect, Instrumentation and messaging.
- Aspect provide method interceptors(method ke pehle ya baadme koyi kaam karna ho) & pointcuts(jisse hum code ko decouple kar pave.)
- messaging aap baanane ke liye use hota hai.
### Data Integration layer.
- Object Realtional Mapping
- Object Xml mapping.
- Orm ye ek integration layer provide karta hai.
    - yadi aapko hibernate apne application mein use karna raha so ye layer se possible ho jata.
### Web module
- web oriented feature provide karta.
### Test module
- Unit testing like JUNIT and mokito.
# 4. Spring IOC container.
![alt text](image-12.png)
- Spring ke sath hume ek component/container milta hai, jise hum Spring IOC  container kehte hai.
- It is responsible for.
    - Basically ye object ko create karta.
    - hold that object in memory
    - whenever require ye inject karta dependency.
- Basically it manage the life cyle object.
#### So spring container is a predefined program which manage the life cyle of object.
![alt text](image-13.png)![alt text](image-14.png)
# 5. Ways of Injecting dependency.
![alt text](image-15.png)
- As per above dig, Student class depend hai Address class ke object ke upar
- So IOC container sabse pehele Address class ki sari value set/intitialize  karke uska object create Karenga.
- Phir Student class ka object create karte hue, uski  id aur name initialize karenge and Address class ki object inject Karenga Student class attribute address mein.
- is tarah se student class ka bean i.e object create honga. Jise hum use kar sakte hai.

![alt text](image-16.png)![alt text](image-17.png)
- For Setter Injection
    - aapko apne class mein Setter methods define karni hongi.
- Object create karte waqt container call karenga setter methods.
    - Address class ka object create karte waqt container uski setter method call karke sari value initialize kar lenga.
- Similarly Student object create karte waqt IOC container call karenga setter method but jab setAddreess() method call karenga so waha IOC container Address class ki dependency inject kar denga.

![alt text](image-18.png)
- Constructor injection ke liye aapko class mein constructor likhna  honga.
- Object create  karte waqt IOC Conatiner constructor call karenga instead of setter method.
    
![alt text](image-19.png)![alt text](image-20.png)![alt text](image-21.png)![alt text](image-22.png)
# 6. Practical

