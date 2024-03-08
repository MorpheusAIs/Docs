# Morpheus Yellow Paper
এই পেপারটি Morpheus এর টেকনিক্যাল বিশদ, Morpheus স্মার্ট কন্ট্রাক্ট, এবং সম্পর্কিত প্রুফ সম্পর্কে বিবরণ করে।
এটি মর্ফিউস, ট্রিনিটি এবং নিও নামে অজানা ডেভেলপারদের অবদানের মধ্যে লেখা হয়েছে। লেখাপত্রের লিঙ্ক এখানে: https://github.com/SmartAgentProtocol/SmartAgents/blob/main/MorpheusWP.md

## মরফিউসের স্থানীয় সংস্করণ 0.0.5 সর্বসাধারণে ব্যবহার হয়:
**Morpheus সংস্করণ 0.0.5 এর জন্য Mac**
- ডাউনলোড করুন গুগল ড্রাইভ থেকে: https://drive.google.com/file/d/1x-wR4HWjKqT_g6VRjrWPXu3rVm9ukOc9/view?usp=sharing
- যাচাইকরণের জন্য SHA 256 হ্যাশ: 9092d543023fb95086cf4a7039d42cbcbbdf5283d670c4de6396b3d89e57b064
- সংস্করণ: Morpheus-0.0.5-x64.dmg

**Morpheus সংস্করণ 0.0.5 এর জন্য Linux Debian**
- ডাউনলোড করুন: https://drive.google.com/file/d/1PQ3n7LXeJHe_jmkYLDUQ9fWjZQTWbHCB/view?usp=sharing
- নির্দেশিকা: ইনস্টল করতে, এই কমান্ড চালিয়ে দিন: sudo dpkg -i /path/to/your/morpheus.deb নোট: উপরের কমান্ডে, "/path/to/your/morpheus.deb" প্রতিস্থান করুন আপনার morpheus_0.0.5_amd64.deb ফাইলের পথের সাথে।
- যাচাইকরণের জন্য SHA হ্যাশ: b227e7bcb21ec9e8e2b4bf9510a2e1f224953fe5 সংস্করণ: morpheus_0.0.5_amd64.deb


First interaction with Morpheus October 22nd 2023.
![FirstInteractionWithMorpheus20231022](https://github.com/MorpheusAIs/Morpheus/assets/1563345/35509f3a-4346-4f58-bb60-f7881fd10f7e)

## মরফিউস স্মার্ট কন্ট্রাক্ট

মরফিউস স্মার্ট কন্ট্রাক্ট দ্বারা যাচাইযোগ্য হতে বলা যায় চেইনে কার্যক্রমগুলি।

1. N2 Yield স্মার্ট কন্ট্রাক্টের ফর্ক আর্বিট্রামে পুনরায় প্রতিষ্ঠাপন
- A) থরচেইন মাধ্যমে ETH লক করুন, কোডারদের + কম্পিউট প্রয়োগকারীদের ইয়েল্ডে অনুদান করুন।
- B) অনুদান করা ইথর এর প্রো-রাতা গণনা

2. MOR এর চিরকাল যাচাইযোগ্য ধ্বংস
- A) MOR টোকেনের জন্য বার্ন ঠিকানা বা বার্ন ফাংশন। মোর ইস্যু করার জন্য ERC20 টেমপ্লেট কন্ট্রাক্ট
- B) প্রতিদিন ক্যাপিটাল + কমিউনিটির প্রো-রাতা অনুদান করতে প্রতিদিন MOR টোকেন মিন্ট করুন।
- C) কোডারদের + কম্পিউট প্রয়োগকারীদের প্রো-রাতা এমওআর টোকেন প্রতিদিন ফি মাধ্যমে বার্ন করতে প্রতিদিন MOR টোকেন মিন্ট করুন।

3. মরফিউস সুরক্ষা নিশ্চিতকরণ - গোপনীয়তা, ওপেন সোর্স, এবং নিরাপত্তা প্রদর্শন করুন
- A) যাচাইযোগ্য এজেন্টদের এবং তাদের স্মার্ট র্যাঙ্ক স্কোরের তালিকা প্রকাশ করুন।
- B) যাচাইযোগ্য LLM এর তালিকা প্রকাশ করুন এবং তাদের স্মার্ট র্যাঙ্ক স্কোর।
- C) স্মার্ট কন্ট্রাক্টগুলির এবং তাদের স্মার্ট র্যাঙ্ক স্কোরের তালিকা প্রকাশ করুন।
- D) প্রোম্পট এবং তাদের স্মার্ট র্যাঙ্ক স্কোরের তালিকা প্রকাশ করুন।
4. সুরক্ষা তহবিল
- A) হ্যাক, ত্রুটি, বাগ, বা অন্যান্য আক্রমণের কারণে লস হওয়ার ক্ষেত্রে মোর এবং ইথ বিতরণ করুন।
- B) পরিভাষিত পরিস্থিতির জন্য প্রিপাইনড সেট। অত্যন্ত গতিতে ফর্ক / রোলব্যাক এর জন্য নীতিসমূহ।
- C) Developers in charge of determining cases of attacks & their remedies. 
- D) Funds for bug bounties / white hat hackers.
- E) Funds for protection from Nation State actors.

## Morpheus Smart Contract Diagrams
মরফিউস স্মার্ট কন্ট্রাক্ট ডায়াগ্রাম
প্রয়োজনীয় স্মার্ট কন্ট্রাক্টগুলির বিবরণ
ETH বিতরণের ডায়াগ্রাম বিস্তারিত করা

### Morpheus MOR Smart Contract Rewards Distribution
![new-buckets](https://github.com/SmartAgentProtocol/SmartAgents/assets/76454555/cd57bae7-2a56-4a55-bf3e-1f810f3fba9c)

### MOR Token Distribution Example of Day 1 and Day 2.
![Untitled spreadsheet - Google Sheets 2023-10-15 13-28-08](https://github.com/MorpheusAIs/Morpheus/assets/76454555/6ff7869d-bbd6-46b5-8673-6a59b75906e1)

## Example Distribution Calculation For Address 0x123 ETH Contributor

### Step One
![Diagram1ofETHDontator](https://github.com/SmartAgentProtocol/SmartAgents/assets/1563345/fead528c-d628-449e-a3a3-2f53904f4a3d)

### Step Two
![ETHGivenDiagram2](https://github.com/MorpheusAIs/Morpheus/assets/1563345/915020e8-d342-48bc-85ee-367de0325680)

### Step Three
![Diagram3ForETHGiven](https://github.com/MorpheusAIs/Morpheus/assets/1563345/a3f455af-56de-4c6b-9688-5b9e91673e5a)

## Example Distribution Calculation For Address 0x123 Compute Provider

### Step One
![MORForCompute](https://github.com/SmartAgentProtocol/SmartAgents/assets/1563345/bef69c69-0420-441f-97f0-7e8195844f57)

### Step Two
![MORForCompute2](https://github.com/SmartAgentProtocol/SmartAgents/assets/1563345/a6f30da5-5441-4f0a-be80-c5798f5920cd)

### MOR Token Distribution Pie Chart
![mordist](https://github.com/MorpheusAIs/Morpheus/assets/76454555/4157efe7-6abf-404a-87f9-a8dc76cd4799)

## Morpheus Developer Tools and Tech Stack.
- Llama2 - সক্ষম ওপেন সোর্স LLM যা স্থানীয়ভাবে চালানো হয়।
- Ollama - Llama2 এর সহজ ইনস্টলেশনের জন্য প্যাকেজিং।
- LangChain - ডেভেলপার টুল, ভেক্টর স্টোর এবং API গুলিতে LLM সংযোগের জন্য।
- LangSmith Editor - LangChain উপরে এজেন্ট তৈরির জন্য লো কোড।
- SmartContractRank অ্যালগরিদম - উদ্দেশ্যে ভিত্তিক ব্যবহারকারীর জন্য স্মার্ট কন্ট্রাক্ট ক্যুরেটিং।
- AgentRank অ্যালগরিদম - ব্যবহারকারীর জন্য ক্ষমতাশালী এজেন্ট ক্যুরেটিং।
- PromptRank অ্যালগরিদম - প্রোজেক্টেড উদ্দেশ্য / অ্যাকশনের উপরে ব্যবহারকারীদের জন্য প্রম্প্ট ক্যুরেটিং।
- Filecoin - স্টোরেজ এবং ক্লাউড কম্পিউট প্রোভিশন।
- Akash Network - LLM / এজেন্ট চালানোর জন্য ওপেন কম্পিউট নেটওয়ার্ক।
- ওয়ালেট - শেপশিফট, এক্সোডাস, অন্যান্য ওপেন সোর্স বিকল্প।

## Morpheus Full Node Diagrams for the Agent / LLMs For Web3 Actions. 
এজেন্টদের পরিদর্শন কোডারদের দ্বারা অনুষ্ঠিত হয়, এটি "এজেন্ট প্রুফ" উত্পন্ন করে যে এজেন্টের বর্ণিত কার্যক্রমগুলি যেমন প্রদর্শিত তেমনি এবং তাতে কোনও দুর্জন কোড নেই।

পরীক্ষার প্রক্রিয়ার বর্ণনার জন্য একটি

## Morpheus User & Contributor Diagram
![Morpheus User   Contributor Diagram](https://github.com/MorpheusAIs/Morpheus/assets/1563345/2cff8d70-c116-472f-a431-8a82bfa22f9b)

### Diagram shows the UX flow from user prompt to approval of Web3 action.
![UX flow for prompted web3 tasks and ticketing](https://github.com/MorpheusAIs/Morpheus/assets/76454555/942b20fb-d67e-4a57-af2c-cd24a89690a5)

### Diagram shows the Morpheus Local install version.
![MorpheusLocalDiagram](https://github.com/SmartAgentProtocol/SmartAgents/assets/1563345/a0564914-cddb-42e4-b0f4-8c2310db6a66)

### Diagram shows the Morpheus P2P install version.
![MorpheusP2PDiagram](https://github.com/SmartAgentProtocol/SmartAgents/assets/1563345/a7eeb31f-3d38-4233-a45f-e9b91ad84ba2)

### Diagram shows the Morpheus Decentralized version.
![MorpheusDecentralized](https://github.com/SmartAgentProtocol/SmartAgents/assets/1563345/1699f2de-cc18-42e8-a05c-32b3307baa20)

## Community
- স্মার্ট এজেন্সি - মরফিউস ব্যবহারকারীদের জন্য ব্যবহারের ক্ষেত্র / এজেন্ট তৈরি করা ফ্রিল্যান্স ডেভেলপারদের দল।
- লোবাল ডেভেলপার কমিউনিটি - বিকাশশীল ডেভেলপার, স্টার্টআপ এবং ব্যবহারকারী কমিউনিটি।
- সম্প্রদায়ী সংগঠন - মরফিউস ডেভেলপারদের, কম্পিউট এবং সম্প্রদায়কে ইথিরিয়াম ধারকদের জন্য আবদ্ধকরণ সংগ্রহ করার জন্য সম্প্রদায় নিয়োগ দেওয়া।
- বিতস্তৃত উন্নয়ন গ্রুপ - স্মার্ট কন্ট্রাক্ট ডেভেলপারদের মরফিউস স্মার্ট কন্ট্রাক্ট কোড করার জন্য।
- মরফিউস ড্যাপস - ব্যবহারকারীর স্মার্ট এজেন্টের সাথে মরফিউস ইন্টিগ্রেশনের জন্য বাজার।