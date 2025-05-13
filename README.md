# GmailGPT
_2023 Spring semester - Independent Study_
### The Ultimate Gmail Assistant Chrome extension
<img width="600" alt="Screenshot 2025-05-12 at 9 54 04 PM" src="https://github.com/user-attachments/assets/db0b6717-b521-469d-852c-6b6ad48f80a2" /><img width="400" alt="Screenshot 2025-05-12 at 9 50 59 PM" src="https://github.com/user-attachments/assets/3b0e7b31-9479-4b05-b340-e9f23ccc3a30" />

### Step 1: Save API Secret Key
<img width="600" alt="Screenshot 2025-05-12 at 9 50 00 PM" src="https://github.com/user-attachments/assets/b755e5b7-326f-4123-88d2-02f1f0022ed9" />

ChatGPT operates using OpenAI's public APIs, which requires users to have an OpenAI account. After creating an account and generating a secret API key, users can enter this key on the GmailGPT settings page. To ensure the security and protection of the API key, we store this data locally using the Chrome storage API. This API has a quota limitation of approximately 5MB, but since we only need to store a short string, it fits our requirements perfectly.

The Chrome storage API has two primary use cases: storage.local and storage.sync. The main difference between them is that storage.sync synchronizes data across all Chrome browsers where the same user is logged in, while storage.local keeps data local to the user's current Chrome browser. We chose storage.local for security reasons, as it ensures that data remains in the user's local browser. The data is saved securely unless the extension is removed.

One improvement we are planning is to implement the OAuth flow so that users don’t need to manually input their API key. With the OAuth flow, we would be able to obtain a refresh token once users log into ChatGPT and successfully use it to call the API, thereby creating a more user-friendly experience.

We make sure the API key is valid by a test API call and verify that we receive a 200 OK response. If the key is found to be invalid, we display a modal to notify the user of the issue.
 

### Step 2: Generate a Email response
<img width="600" alt="Screenshot 2025-05-12 at 9 50 34 PM" src="https://github.com/user-attachments/assets/fc02e079-3b1e-4604-9346-2edb1d80fc18" />

The user can input two fields: the email prompt and the desired tone.
The email prompt specifies the subject or purpose of the email. Here are a few examples of possible prompts:

- Write an email that confirms my interview availability this Friday at 2pm
- Write an email that requests an extension for my philosophy midterm paper.
- Write an email that informs my team about a change in the scheduled meeting time.
- Write an email to schedule a follow-up meeting after a client presentation.

By providing these prompts, users can receive a basic outline for their email. We are also aware that the tone of the email should depend on the context and the recipient. Currently, we offer the tones: concise, professional, confident, nice, passionate, apologetic. The user can choose one or more tones that best align with their intentions. GmailGPT then leverages the chosen tones and prompts to generate a customized email suited to the user's needs.

For example, the following email is generated using “Write an email to schedule a follow-up meeting after a client presentation.” prompt and concise and professional tones.
```
Dear [Client's Name],

I hope you are doing well. Thank you for attending our recent presentation. We appreciate your time and attention.

We would like to schedule a follow-up meeting to further discuss your interests and how our services can benefit your organization. Please provide your availability over the next two weeks so we can find a suitable time for both parties.

Let us know if you prefer an in-person or virtual meeting format, and we will make the necessary arrangements.

Thank you for your consideration. We look forward to our next interaction.

Best regards,
[Your Name]
[Your Title]
[Your Company]
```

The following email is generated using the same prompt, but using nice and passionate tones.
```
Dear [Client's Name],

I hope this email finds you well. I wanted to express my gratitude for your time and attention during our recent presentation. Your engagement and insightful questions truly inspired our team, and we are eager to continue the conversation.

In light of our productive discussion, I'd like to propose scheduling a follow-up meeting to dive deeper into the aspects that piqued your interest and to further explore how our services can benefit your organization. We are passionate about delivering exceptional results and are excited about the prospect of working together.

Please let me know your availability over the next two weeks, and I will be more than happy to coordinate a time that is convenient for both parties. If you have any preferences regarding the meeting format, whether in-person or virtual, kindly share them as well, and we'll accommodate accordingly.

Once again, thank you for your enthusiasm and consideration. We are truly looking forward to our next interaction and the opportunity to build a strong, collaborative partnership.

Warm regards,
[Your Name]
[Your Title]
[Your Company]
```

### Step 3: Insert to Email
<img width="600" alt="Screenshot 2025-05-12 at 9 50 59 PM" src="https://github.com/user-attachments/assets/3b0e7b31-9479-4b05-b340-e9f23ccc3a30" />
<img width="600" alt="Screenshot 2025-05-12 at 9 51 26 PM" src="https://github.com/user-attachments/assets/e563cfa4-0fbd-4a8b-aabf-cfb45badd867" />

Users can simply click the insert button or copy the text to insert to Email.
