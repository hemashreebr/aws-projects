# AI-Powered Translation Assistant using AWS Bedrock

This project is a **translation assistant** powered by **AWS Bedrock** and **Streamlit**. It allows users to input text, select source and target languages, and translate using AI foundation models (Anthropic Claude models, Stability AI models, etc.).

---

## **Features**

* Translate text between multiple languages
* Use Anthropic or Stability AI foundation models in AWS Bedrock
* Evaluate translation accuracy
* Interactive web interface using Streamlit

---

## **Prerequisites**

* Basic knowledge of **AWS** and **Python**
* AWS account with **Bedrock access**
* Python 3.11 installed on your system
* `pip` package manager

---


![Architecture](images/translatearch.png)

---

## **Step-by-Step Setup**

### **1. Clone the Repository**

```bash
git clone https://github.com/aws-samples/AWS-First-GenAI-Journey.git
cd AWS-First-GenAI-Journey/AWS-AI-Powered-Translation-Assistant
```

### **2. Create a Python Virtual Environment**

```bash
python3.11 -m venv translate3
source translate3/bin/activate   # Mac/Linux
translate3\Scripts\activate      # Windows
```

### **3. Install Required Packages**

```bash
pip install -r requirements.txt
```

### **4. Configure AWS CLI**

Make sure your AWS credentials have **Bedrock access**:

```bash
aws configure
```

* Set your AWS Access Key, Secret Key, and default region (`us-east-1`).

Test access to Bedrock models:

```bash
aws bedrock list-foundation-models --region us-east-1
```

* You should see a JSON list of available models.

### **5. Update Streamlit App with Available Models**

* Open `Text.py`
* Update the code to select one of the **active Bedrock models** from your CLI output, for example:

  * `anthropic.claude-haiku-4-5-20251001-v1:0`
* Ensure default selection in Streamlit matches a model that exists in your account.

### **6. Run the Streamlit App**

```bash
streamlit run Text.py
```

* Open the displayed **Local URL** in your browser
* Input text, select source and target languages, and translate

---

## **Usage**

1. Choose **Source Language** from the sidebar
2. Choose **Target Language**
3. Choose **Bedrock Model**
4. Enter text in the chat box
5. Click **Translate**
6. View **Translation Output** and **Analysis**

---

## **Tips & Notes**

* Use **Python 3.11** for compatibility
* Ensure **AWS Bedrock permissions** are correct
* Streamlit interface is interactive, you can **clear past messages** using the sidebar button
* Only select **active models** from your Bedrock account

---

## **References**

* [AWS Bedrock Documentation](https://docs.aws.amazon.com/bedrock/latest/userguide/what-is-bedrock.html)
* [Streamlit Documentation](https://docs.streamlit.io/)
* [AWS CLI Bedrock Commands](https://docs.aws.amazon.com/cli/latest/reference/bedrock/index.html)

