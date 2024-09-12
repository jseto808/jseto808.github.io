---
layout: essay
type: essay
title: "Am I Asking Smart Questions?"
# All dates must be YYYY-MM-DD format!
date: 2024-09-11
published: true
labels:
  - Smart Questions
  - Smart Answers
  - StackOverflow
---

<img width="500px" class="rounded float-start pe-4" src="../img/smart-questions/Stupid-Question.jpg">

## What are Stupid Questions?
At some point in our lives, most of us have heard someone say, "There are no stupid questions." This is wrong. Some questions can be considered stupid because they often lack the characteristics of a smart question, which leads to wasted time and frustration. Attributes of a stupid question are typically: 

1. Lack of Preparation: Stupid questions are frequently asked by individuals who have not invested time in preliminary research. Questions that could be answered with a simple search or a basic understanding of the topic indicate a lack of effort. For example, asking "What does the term 'open-source' mean?" in a technical forum where this concept is fundamental might be seen as a lazy approach.

2. Vagueness and Ambiguity: Stupid questions are often vague and do not provide enough information for others to give a useful response. Questions like "Why does this not work?" without any context or details fail to elicit meaningful help. Providing specific details about what is being attempted and the exact nature of the problem is crucial.

3. Irrelevance: Questions that are off-topic or irrelevant to the current discussion or forum can be perceived as stupid. For example, asking about the best way to cook pasta in a programming forum is not only irrelevant but also disruptive to the topic at hand.

4. Disrespectful or Demanding Tone: Questions that come across as rude, demanding, or entitled can alienate respondents. Statements like "You need to solve this problem for me" are not only unproductive but can also be perceived as disrespectful.

## What are Smart Questions
On the other hand, smart questions can be characterized by their clarity, relevance, and thoughtful consideration of the context. Some key elements of a smart question are:

1. Preparation and Research: Smart questions are preceded by adequate preparation. This means the asker has done some preliminary research and has a basic understanding of the topic. They avoid asking questions that can be easily answered by a quick search or by reviewing readily available resources. For instance, instead of asking, "How do I fix this error in my code?" a smart question would be, "I encountered this specific error while following these steps in my code. I have tried these solutions, but the problem persists. Here’s the error message and my code snippet—what might be going wrong?"

2. Specificity: Smart questions are precise and focused. They clearly define the problem or area of inquiry. This specificity helps others to provide accurate and relevant answers. For example, asking, "How can I improve my programming skills?" is less effective than, "What are some best practices for writing clean and efficient Python code?"

3. Context and Relevance: A smart question considers the context of the discussion or the expertise of the audience. It is framed in a way that makes it relevant to the current conversation or the specific knowledge of the people being asked. By tailoring questions to the context, the asker demonstrates an understanding of the subject matter and shows respect for the respondents’ time and expertise.

4. Politeness and Professionalism: Politeness and a respectful tone are hallmarks of a smart question. Even when frustrated, a smart question is framed in a way that acknowledges the effort of the respondents. For instance, "I’m having trouble with this issue and would greatly appreciate your advice" is more likely to elicit a helpful response than a terse, "Why isn’t this working?"

## How to Ask a Smart Question
This question from Stack Overflow is a great example of a smart question. The asker titled their question: `Java: Need to create PDF from byte array`. The asker is asking for help in creating a PDF out of a byte array. This is a good example of a smart question for several reasons:
1. Specificity and Focus
   - The question is specific about the problem the asker is facing: converting a byte array into a PDF file in Java. This focus allows responders to understand exactly what is needed without needing to guess or seek additional clarification. The specificity of the question—dealing with byte arrays and PDFs in Java—directs answers toward relevant solutions and tools.

2. Contextual Information
   - The question provides a clear context for the problem. The asker provides a copy of their code to provide clear context of what they are trying to achieve:
```
     static void byteArrayToFile(byte[] bArray) {  
    try {  
        // Create file  
        FileWriter fstream = new FileWriter("out.pdf");  
        BufferedWriter out = new BufferedWriter(fstream);  
        for (Byte b: bArray) {  
            out.write(b);  
        }  
        out.close();  
    } catch (Exception e) {  
        System.err.println("Error: " + e.getMessage());  
    }  
}
```

3. Demonstrates Effort
   - The asker demonstrated that they have tried to solve this problem on their own and have provided the steps that they have taken to solve the problem on their own:
     - `I was actually able to create the correct PDF by writing a web application using essentially the same process. The primary difference between the web application and the code about was this line:`
```
response.setContentType("application/pdf");
```

4. Clear Objective
   - The goal of the question is clearly stated: to create a PDF from a byte array. This clarity helps responders focus on providing a solution that meets the exact needs of the asker. It avoids ambiguity and ensures that the answers are relevant to the problem at hand.
  
Due to the question being a smart question, the answers were able to be concise. The answers given all show simple lines of code that could help the asker solve their problem:
```
OutputStream out = new FileOutputStream("out.pdf");
out.write(bArray);
out.close();
```

Source: <a href="https://stackoverflow.com/questions/1777914/java-need-to-create-pdf-from-byte-array"><i class="large github icon "></i>Smart Question</a>

## Guide on What Not to Do
On the other hand, another question from Stack Overflow can demonstrate what not to do when asking a question. The asker of this question is trying to ask how to send 100,000 emails every week using PHP. This is an example of a stupid question because it lacks specifics and shows a lack of prior research. Overall the characteristics that make this a stupid question are:
1. Lack of Specificity
   - The question is very broad and lacks specificity. It does not detail the context or constraints, such as:
     - Purpose: What is the goal of sending 100,000 emails? Is it for marketing, notifications, or something else?
     - Technical Details: What kind of email system or infrastructure is being used or considered? Are there existing constraints or requirements?
     - Programming Language: Are there any specific technologies, frameworks, or programming languages in use?
   - Without this crucial information, it is challenging for responders to offer precise and helpful solutions. The broad nature of the question makes it difficult to provide a targeted response that applies to the asker’s situation.

2. Lack of Prior Research
   - Good questions typically demonstrate that the asker has done some initial research or attempted to solve the problem themselves. This question may come across as lacking in effort, as it does not reflect any prior attempts or research into handling high-volume email sending. This can give the impression that the asker is seeking a broad overview rather than a specific coding solution.

3. General Advice vs. Specific Solutions
   - On Stack Overflow, the expectation is that questions are well-defined and focused on specific technical issues related to programming. This question is more about general advice on managing email campaigns, which may not align well with the site’s focus on programming solutions. It could potentially be better suited for a marketing or IT operations forum where questions about email campaigns and delivery management are more appropriate.

This is why the answers to this question are all long answers that have multiple different ways to solve the problem. Due to the lack of specifics, it is hard to provide an answer that is specific to the asker's problem and situation.


Source: <a href="https://stackoverflow.com/questions/3905734/how-to-send-100-000-emails-weekly"><i class="large github icon "></i>Stupid Question</a>

## Conclusion
The distinction between smart and stupid questions is not merely a matter of content but also involves how questions are framed and delivered. Smart questions are well-researched, specific, contextually relevant, and politely phrased. They contribute constructively to discussions and facilitate problem-solving. In contrast, stupid questions often reflect a lack of effort, clarity, or relevance, and can hinder progress and communication. Understanding these principles helps individuals ask more effective questions, thereby enhancing their learning experiences and contributing positively to collaborative environments. By adhering to the guidelines of asking smart questions, one not only gains more accurate and useful answers but also fosters a more respectful and productive discourse.
