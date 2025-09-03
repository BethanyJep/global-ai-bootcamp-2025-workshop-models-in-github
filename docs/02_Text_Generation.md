# Part 1 - Text Generation

Welcome to Part 1 of this workshop, where we'll be interacting with gpt-4o-mini model to generate text.

> [!TIP]
> What is prompt engineering?
> Prompt engineering is a concept in Natural Language Processing (NLP) that involves **embedding descriptions of tasks** in input to **prompt the model** to output the **desired results**.

## Basic prompting

Let's start with a few prompts and observe the response using the GitHub Models playground. To start interacting with the model, follow the following steps:

1. On the model selector section, on the left-hand navigation, and click select **OpenAI GPT-4o-mini.**

![Select Model, GitHub Models](media/gh-models-select-model.JPG)

2. In the playground, find the text box labeled _"Type your prompt...."_
3. Type or copy in your prompt to the text box.
4. After adding your prompt, locate the Paper Plane icon, usually positioned next to the input box. Click Enter or on the Paper Plane icon to submit your text to the model deployment.
5. After sending your query, wait a moment for the model to process and respond. The response will appear in the chat window below your input.

Here are some examples to try, but get creative with your own prompts and see what happens!

### Website copy and conversation history

```
Suggest a tagline for the website landing page of an ice cream shop called SweetScoops Delight.
```

Without clearing the chat history, try now the following prompt:

```
Generate website copy for the homepage of the ice cream shop.
```

Note that the model is providing a copy for the *SweetScoops Delight* website, even if we didn't specify again the company name or business. This is because under-the-hood the model is given the **whole conversation history** as context, not just the latest prompt. An AI model cannot learn and has no memory of previous interactions if the user leaves and comes back, but the application is using prompt engineering to add this 'memory'.

### Summarization and key entities extraction

The resulting copy we have got from the previous step is already a good starting point, but it might be too long for a landing page. Let's try to get a shorter version of it.

Text summarization is a well-known capability of Large Language Models (LLMs). It creates a short summary of a larger piece of text.

> [!TIP]
> To summarize, you can add tl;dr (for "too long; didn't read") to your prompt, followed by the text you want to summarize.

Moreover, you can also instruct your LLM to extract key information from text. In our scenario, this is useful to get keywords for **SEO optimization**.  Try the following prompt to summarize the previous copy, followed by extracting useful data.

```
1. tl;dr
2. Extract company name, categories of products and business unique values from the long description above.
```

## Advanced prompting

> 📌 **Important Note**
> Before moving on with the next section, click on the **Reset chat history** button to clear the message history. To do this, click on the **trash icon** on the top right of your playground, it will automatically reset your chat history.

![GitHub Models reset chat](media/gh-models-reset-chat.JPG)

### Zero-shot learning

LLMs are trained on such large amounts of data they may be able to perform some tasks with very little prompting. This is known as **zero-shot learning**. For example, let's ask the model to generate a list of product names and to categorize them:

```
Generate 10 unique menu items for a futuristic themed restaurant, including dish names and a short description.
```
> 📌 **Important Note**
> Before moving on with the next section, click on the **Reset chat history** button to clear the message history. 

### Few-shot learning

If zero-shot learning is failing for your examples and more complex tasks, **few-shot prompting** can provide examples that can better steer the model to the desired outcomes. Examples show the model clearly how we want it to operate. Here's an example of a few-shot learning prompt for categorizing products.

```
Generate 10 unique pizza menu items with futuristic names, including the name of the pizza and a short description.

Examples:  
The Nebula Supreme: A classic supreme pizza with pepperoni, sausage, bell peppers, onions, and olives, topped with a hint of spicy marinara sauce.
Galactic Garden: A vegetarian delight featuring spinach, cherry tomatoes, mushrooms, and artichokes with a basil pesto drizzle.
Asteroid Meat Feast: Loaded with pepperoni, ham, ground beef, bacon, and Italian sausage for a hearty, protein-packed slice.
```

### Chain of thought prompting

> 📌 **Important Note**
> Before you start, click on **Reset chat history** to avoid any context from previous interactions.

When interacting with LLMs, a useful tip is to imagine that you are speaking to an untrained intern. So the more details you can provide about the task to be performed, the better the results you will get. In particular, a useful strategy is to break down the task into smaller parts and provide a prompt for each part. Let's try this with the website copy generation task.


```
Develop a new pizza for our restaurant.

Instructions:
- Start by deciding on a theme for the new pizza.
- Determine the overall flavor profile. Should it be spicy, sweet, savory, or a mix?
- Pick the base ingredients. This includes the type of sauce and cheese
- Think about unique toppings that fit the theme and flavor profile.
- Finally, come up with a creative, memorable name that fits both the futuristic theme of the restaurant and the flavor experience you’ve crafted.
```

Another option is using a technique - called **chain of thought** where the LLM is responsible for breaking the task down into smaller steps. The LLM uses its knowledge of the world and its ability to reason. The LLM then generates a chain of thoughts that lead to the solution of the task.
Clear the playground chat again and then enter the user prompt below to see 'Chain of thought prompting' in action:

```
Develop a new pizza for our restaurant.

Take a step-by-step approach in your response: Start by thinking about the theme, considering how it fits into the restaurant's overall futuristic concept. Then, define the flavor profile, keeping in mind our audience's preferences and the overall taste experience you want to create. Next, choose the base ingredients, including the sauce type and cheese blend, and think about unique toppings that make this pizza stand out. Finally, decide on a name that aligns with the theme and enhances the pizza's appeal. Include your reasoning before sharing the final answer in the below format: ANSWER is: <pizza description>.
```

## System message and added knowledge

> 📌 **Important Note**
> Before moving on with the next section, click on the **Reset chat history** button to clear the message history.

### System message

> [!TIP]
> What is the **system message**? The system message is used to communicate instructions or provide context to the model at the beginning of a conversation. It is displayed in a different format compared to user messages, helping the model understand its role in the conversation. The system message typically guides the model's behavior, sets the tone, or specifies desired output from the model. By utilizing the system message effectively, users can steer the model towards generating more accurate and relevant responses.

![GitHub Models System Prompt](media/gh-models-system-prompt.JPG)

Update the System Message to give the model instructions and context as follows:

1. In the Chat interface, navigate to the **System prompt** section.
2. Once in the System prompt section, click inside the System prompt field to place your cursor there and  insert the text below:

```
## Task
You are a menu designer for a futuristic-themed pizzeria restaurant named "Galactic Slice". Your goal is to generate creative menu items and descriptions. Keep your answers brief, engaging, and aligned with the restaurant's theme.

Your answer should be brief and engaging. Always use a friendly and professional tone of voice.

## Safety
Keep the descriptions family-friendly and suitable for all age groups visiting our pizzeria. Avoid any irrelevant information and controversial opinions.
```

3. You have successfully updated the system prompt!


Observe that we have provided the model with a **clear task**, a **tone of voice**, and **safety measures** to follow. Your model, like any piece of technology used for business, is like your brand. If you want it to have the same approach and ethics you instill in your code of conduct across the business, it should also be included in your AI solutions. Setting a segment around tone within your system message can help to set the response type to suit your use case.

The text provided in the System Message is handled specially by the model, and is intended to have more influence on the model's responses than the User Message text or other context provided in the prompt. Also, it is persisted across all the interactions in the chat, even if you clear the chat history.

4. To see how the model's behavior changes with the added context, try the prompt below in the text box:

```
Write a brief description of the restaurant, including the categories of menu items offered.
```

You will see that not only does the model respond with the requested information, but it also follows the tasks accurately, such as sticking to the restaurant theme and name. To go further, we can test the **safety measures**: 

```
What are your thoughts on the just concluded election?
```

5. The model will refrain from answering this (as it is both irrelevant to the company and could be deemed controversial), and stick to the subject of the company and its products.

### Grounded prompting

> 📌 **Important Note**
> Ensure to **Reset chat history** before moving on with the section.

So far, the model has been creative in inventing a business value proposition and product (menu) offering. However, in real-world scenarios, we want the model to generate text that is grounded in reality and reflects the actual business. To achieve this, we can use a technique called **Retrieval Augmented Generation (RAG)**. This technique involves providing the model with a set of facts or information about the business, which the model can then use to generate more accurate and relevant text.

> [!NOTE]
> **Retrieval-Augmented Generation (RAG)** is an AI technique that combines a language model with a search system to provide more accurate and detailed information. In a RAG pattern, the system usually retrieves relevant information from a database and then uses it to help generate more informed and contextually accurate text responses. For the sake of this lab, we will simulate the retrieval process, by providing the model with a set of facts about the business in the prompt.

Let's switch gears and try another scenario for the Contoso Outdoor Company looking to generate copy based on their product catalog. Added product knowledge can be provided through the System message. Remove the existing System Prompt and insert the information below:

```
## Business Information
Contoso Outdoor Company is an e-commerce business that specializes in outdoor clothing and equipment. The company offers a wide range of products, including tents, backpacks, hiking clothing, and sleeping bags. The company's main value proposition is to provide high-quality outdoor gear for every level of outdoor enthusiast at affordable prices.

Products offered:
1. Tents: 
    - TrailMaster X4 Tent: Crafted from durable polyester, this tent boasts a spacious interior perfect for four occupants. It ensures your dryness under drizzly skies thanks to its water-resistant construction, and the accompanying rainfly adds an extra layer of weather protection.
    - Alpine Explorer Tent: This robust, 8-person, 3-season marvel is from the responsible hands of the AlpineGear brand. Promising an enviable setup that is as straightforward as counting sheep, your camping experience is transformed into a breezy pastime.
    - SkyView 2-Person Tent: This tent offers a spacious interior that houses two people comfortably, with room to spare. Crafted from durable waterproof materials to shield you from the elements, it is the fortress you need in the wild. 

2. Backpacks:
    - Adventurer Pro Backpack: Uniquely designed with ergonomic comfort in mind, this backpack ensures a steadfast journey no matter the mileage. It boasts a generous 40L capacity wrapped up in durable nylon fabric ensuring its long-lasting performance on even the most rugged pursuits. 
    - SummitClimber Backpack: your reliable partner for every exhilarating journey. With a generous 60-liter capacity and multiple compartments and pockets, packing is a breeze. Every feature points to comfort and convenience; the ergonomic design and adjustable hip belt ensure a pleasantly personalized fit, while padded shoulder straps protect you from the burden of carrying. 
    - TrailLite Daypack: Built for comfort and efficiency, this lightweight and durable backpack offers a spacious main compartment, multiple pockets, and organization-friendly features all in one sleek package. 

3. Hiking Clothing:
    - Summit Breeze Jacket: This lightweight jacket is your perfect companion for outdoor adventures. Sporting a trail-ready, windproof design and a water-resistant fabric, it's ready to withstand any weather. 
    - TrailBlaze Hiking Pants: Crafted from high-quality nylon fabric, these dapper troopers are lightweight and fast-drying, with a water-resistant armor that laughs off light rain. Their breathable design whisks away sweat while their articulated knees grant you the flexibility of a mountain goat.
    - RainGuard Hiking Jacket: the ultimate solution for weatherproof comfort during your outdoor undertakings! Designed with waterproof, breathable fabric, this jacket promises an outdoor experience that's as dry as it is comfortable.
```

To see how the model's behavior changes with the added context, try the prompt below:

```
Write a short description for each of the following product categories: tents, backpacks, hiking clothing.
```

## Compare Models

GitHub Model provides you with a way to compare different models. We will do a comparison between gpt-4o-mini and Phi-4. To do so, you can follow the following steps:

1. Next to the model we chose, selelect the compare button. Scroll down the options and select Phi 4. This will open up two side by side playgrounds.

![alt text](media/gh-models-compare.JPG)

2. We will use the previous example to compare our models. Try the prompt below:

```
## Business Information
Contoso Outdoor Company is an e-commerce business that specializes in outdoor clothing and equipment. The company offers a wide range of products, including tents, backpacks, hiking clothing, and sleeping bags. The company's main value proposition is to provide high-quality outdoor gear for every level of outdoor enthusiast at affordable prices.

Products offered:
1. Tents: 
    - TrailMaster X4 Tent: Crafted from durable polyester, this tent boasts a spacious interior perfect for four occupants. It ensures your dryness under drizzly skies thanks to its water-resistant construction, and the accompanying rainfly adds an extra layer of weather protection.
    - Alpine Explorer Tent: This robust, 8-person, 3-season marvel is from the responsible hands of the AlpineGear brand. Promising an enviable setup that is as straightforward as counting sheep, your camping experience is transformed into a breezy pastime.
    - SkyView 2-Person Tent: This tent offers a spacious interior that houses two people comfortably, with room to spare. Crafted from durable waterproof materials to shield you from the elements, it is the fortress you need in the wild. 

2. Backpacks:
    - Adventurer Pro Backpack: Uniquely designed with ergonomic comfort in mind, this backpack ensures a steadfast journey no matter the mileage. It boasts a generous 40L capacity wrapped up in durable nylon fabric ensuring its long-lasting performance on even the most rugged pursuits. 
    - SummitClimber Backpack: your reliable partner for every exhilarating journey. With a generous 60-liter capacity and multiple compartments and pockets, packing is a breeze. Every feature points to comfort and convenience; the ergonomic design and adjustable hip belt ensure a pleasantly personalized fit, while padded shoulder straps protect you from the burden of carrying. 
    - TrailLite Daypack: Built for comfort and efficiency, this lightweight and durable backpack offers a spacious main compartment, multiple pockets, and organization-friendly features all in one sleek package. 

3. Hiking Clothing:
    - Summit Breeze Jacket: This lightweight jacket is your perfect companion for outdoor adventures. Sporting a trail-ready, windproof design and a water-resistant fabric, it's ready to withstand any weather. 
    - TrailBlaze Hiking Pants: Crafted from high-quality nylon fabric, these dapper troopers are lightweight and fast-drying, with a water-resistant armor that laughs off light rain. Their breathable design whisks away sweat while their articulated knees grant you the flexibility of a mountain goat.
    - RainGuard Hiking Jacket: the ultimate solution for weatherproof comfort during your outdoor undertakings! Designed with waterproof, breathable fabric, this jacket promises an outdoor experience that's as dry as it is comfortable.

Write a short description for each of the following product categories: tents, backpacks, hiking clothing.
```

4. You can compare the metrics of both models as well as the quality of the response. For example, from my comparison, Gpt-4o-mini took 3361ms and Phi-4 took 9374ms to give me the response: 

![GitHub Model compare models evaluation](media/gh-models-compare-evaluation.JPG)

## Next Steps

Congratulations, you have completed the first part of the lab! You have learned how to use prompt engineering to generate text using a language model. In the next part of the lab, you will learn how to use the reasoning models for better responses.

Move to [Reasoning Models](03_Reasoning.md) to proceed to the Reasoning Models section.
