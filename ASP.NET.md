## ASP.NET 
✅ .NET Core এবং .NET Framework এর পার্থক্য, আর্কিটেকচার, মাইগ্রেশন চ্যালেঞ্জ, এবং ডিপ ডাইভ কনসেপ্টগুলো নিচে বিস্তারিত আলোচনা করা হলো: <br> 
.NET Core vs. .NET Framework : <br> 
```
বৈশিষ্ট্য (Feature)            |             .NET Framework                        |      .NET Core / .NET (আধুনিক সংস্করণ)
-------------------------------------------------------------------------------------------------------------------------------------------------------------
আর্কিটেকচার (Architecture)  |  "Monolithic (মনোলিথিক): বিশাল, একক প্যাকেজ।"     |  "Modular (মডুলার): ছোট, স্বাধীন প্যাকেজ (NuGet Packages) এ বিভক্ত।"
প্ল্যাটফর্ম (Platform)         |   Windows Only: শুধুমাত্র উইন্ডোজ অপারেটিং সিস্টেমে চলে।  |  "Cross-Platform: Windows, macOS, এবং Linux-এ চলে।"
ওপেন সোর্স (Open Source)   |   Closed Source: আংশিক ওপেন সোর্স।                  |   Open Source: সম্পূর্ণ ওপেন সোর্স (MIT License)।
পারফরম্যান্স (Performance)  |   তুলনামূলকভাবে কম।                                 |   Significantly Higher: উন্নত JIT কম্পাইলার এবং অপটিমাইজেশনের কারণে অনেক দ্রুত।
বিল্ডিং ব্লক                  |   "Application Domains, System.Web, web.config"     |   "Dependency Injection, Middleware, appsettings.json"
হোস্টিং (Hosting)           |   IIS (Internet Information Services)               |    Kestrel Web Server (Built-in) এবং IIS/Nginx/Apache এর পেছনে।
```
Middleware Pipeline (মিডলওয়্যার পাইপলাইন) : <br> 
.NET Core / .NET এ, প্রতিটি HTTP অনুরোধ একটি Middleware Pipeline এর মধ্য দিয়ে যায়। এটি .NET Framework এর HttpModule এবং HttpHandler কে প্রতিস্থাপন করেছে। <br> 
কাজ: পাইপলাইনের প্রতিটি উপাদানকে Middleware বলা হয়। প্রতিটি Middleware HTTP অনুরোধটিকে পরীক্ষা করে, পরিবর্তন করে বা প্রতিক্রিয়া জানায়, এবং তারপর পাইপলাইনে পরের মিডলওয়্যারকে পাস করে দেয় (অথবা শর্ট সার্কিট করে)। <br> 
গুরুত্বপূর্ণ মিডলওয়্যার (Examples): Exception Handling: ত্রুটি পরিচালনা করে। Routing: অনুরোধটিকে সঠিক এন্ডপয়েন্টে (Controller/Action) রুট করে। Authentication/Authorization: ব্যবহারকারীর পরিচয় এবং অনুমতি যাচাই করে। Static Files: স্ট্যাটিক ফাইল (CSS, JS, images) পরিবেশন করে।
<br> <br> <br> 


--------------------------------------------------------------------
<b>SOLID Principle </b> 
১. S - Single Responsibility Principle (SRP) <br> 
ধারণা: একটি ক্লাস বা মডিউলের পরিবর্তন হওয়ার কারণ (Reason for Change) একটিই হওয়া উচিত। <br> 
২. O - Open/Closed Principle (OCP): <br> 
ধারণা: একটি ক্লাস বা মডিউল এক্সটেনশনের জন্য উন্মুক্ত (Open for extension), কিন্তু পরিবর্তনের জন্য বন্ধ (Closed for modification)। <br> 
৩. L - Liskov Substitution Principle (LSP): <br> 
ধারণা: সাব-ক্লাস (Sub-Class) বা ডেরাইভড ক্লাস (Derived Class) তার বেস ক্লাস বা প্যারেন্ট ক্লাসের কার্যকারিতা পরিবর্তন না করে প্রতিস্থাপনযোগ্য হতে হবে। <br> 
৪. I - Interface Segregation Principle (ISP): <br> 
ধারণা: ক্লায়েন্টদের তাদের ব্যবহার করবে না এমন ইন্টারফেস ইমপ্লিমেন্ট করতে বাধ্য করা উচিত নয়। বড় ইন্টারফেসকে ছোট ছোট, সুনির্দিষ্ট ইন্টারফেসে ভাগ করা উচিত। <br> 
৫. D - Dependency Inversion Principle (DIP): <br> 
ধারণা: হাই-লেভেল মডিউলগুলি লো-লেভেল মডিউলগুলির উপর নির্ভর করবে না। উভয়কেই অ্যাবস্ট্রাকশনের (Abstraction) উপর নির্ভর করতে হবে। অ্যাবস্ট্রাকশনগুলি বিস্তারিত বিবরণের (details) উপর নির্ভর করবে না; বরং বিস্তারিত বিবরণই অ্যাবস্ট্রাকশনের উপর নির্ভর করবে। <br> 


<b>Scalability: Design Patterns for Enterprise Apps:  </b> <br> 
এন্টারপ্রাইজ অ্যাপ্লিকেশন ডিজাইন করার সময় ডেটা অ্যাক্সেস লেয়ারকে (Data Access Layer) বাকি বিজনেস লজিক থেকে আলাদা করার জন্য দুটি মৌলিক প্যাটার্ন ব্যবহার করা হয়। <br> 
১. Repository Pattern (রিপোজিটরি প্যাটার্ন) <br> 
উদ্দেশ্য: ডেটা সোর্স (ডেটাবেস) থেকে অ্যাপ্লিকেশনকে বিচ্ছেদ করা। <br> 
২. Unit of Work (ইউনিট অফ ওয়ার্ক) <br> 
উদ্দেশ্য: একটি একক লজিক্যাল ট্রানজ্যাকশনের মধ্যে একাধিক রিপোজিটরি অপারেশনকে একত্রে গ্রুপিং করা।





----------------------------------------------------------------------------------------------------------

