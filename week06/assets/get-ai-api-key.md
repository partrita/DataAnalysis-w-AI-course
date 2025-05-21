You will need to log in to each provider’s developer console, set up any required billing or credits, and then generate and securely store a long secret string that acts as your API key. For **OpenAI**, you’ll work within the [Platform](https://platform.openai.com/) UI—creating a project, adding prepaid credits, and clicking through to **API Keys** to spin up a new secret key. For **Anthropic**, you’ll use the [Console](https://console.anthropic.com/)—navigating to **API Keys**, clicking **Create Key**, and immediately copying that one-time display of your new key. In both cases, best practices include storing keys in environment variables, never checking them into version control, and rotating or revoking unused keys.

## How to get an API key: OpenAI ChatGPT

### 1. Log in to the OpenAI Platform

1. Go to [https://platform.openai.com/](https://platform.openai.com/) and click **Log in** in the top-right corner, then enter your ChatGPT credentials to sign in.
2. After logging in, you’ll see your profile icon in the top-right corner of the dashboard, confirming your access.
3. Here you will find information about Core Concepts, Tools, Specialized Models, etc.

### 2. Create a Project

1. Then navigate to [https://platform.openai.com/settings/organization/projects](https://platform.openai.com/settings/organization/projects) and click **+ Create**. 
2. Enter a name, then click **Create** to set up a new project. 

### 3. Set Up Billing (Add Prepaid Credits)

1. On the left side navigation menu under **Projects** click **Billing**. 
2. Then, **Add payment details** and enter your credit card information. 
3. Here you can also add credits needed for running the API. The minimum amount you can add is \$5 which is more than enough for our class. 

### 4. Generate and Store Your API Key

1. Navigate to **API Keys**. 
2. Click **+ Create new secret key**, enter a descriptive name (e.g., “Course Project Key”), assign it to the relevant project, and click **Create secret key**. 
3. **Important:** Copy the full API key string displayed and store it in a secure location (such as a password manager). You will not be able to view it again in the console.

### Other Advice

* Rotate or regenerate your API keys regularly and revoke any that are no longer in use to minimize risk. 
* Add each key to your `.gitignore` file to avoid accidental exposure in version control. 
* Consider setting scoped permissions on keys (where available) to limit their capabilities (e.g., restrict endpoints). 

---

## How to get an API key: Anthropic Claude

### 1. Log in to the Anthropic Console

1. Visit [https://console.anthropic.com](https://console.anthropic.com) and click **Sign in** in the top-right corner, then authenticate with your Claude account credentials. 
2. Upon logging in, you’ll land on the Anthropic Console dashboard. 

### 2. Navigate to the API Keys Section

1. In the left-hand navigation menu, click **API Keys** under your account settings.
2. If you don’t see **API Keys**, click your profile icon (top-right) and select **API Keys** from the dropdown. 

### 3. Generate a New API Key

1. Click the **Create Key** button at the top-right of the API Keys page. 
2. In the pop-up, give your key a recognizable name (e.g., “Claude Course Key”) and click **Create Key**. 

### 4. Copy and Secure Your Key

1. The console will display your full API key string once – **copy it** immediately and save it securely (e.g., in a password manager). 
2. Do **not** leave your key exposed in code or public repositories; treat it like a password. 

### Other Advice

* Rotate keys periodically and delete any unused or compromised keys to maintain security.
* Monitor your credit balance and usage in **Plans & Billing** to avoid unexpected costs. 
