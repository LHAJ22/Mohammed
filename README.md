import openai

# أدخل مفتاح API الخاص بك من OpenAI هنا
openai.api_key = 'YOUR_API_KEY'

def welcome_message():
    print("مرحباً! أنا هنا للإجابة على أي سؤال قد يكون لديك.")

def get_ai_response(question):
    response = openai.Completion.create(
        engine="text-davinci-003",  # يمكنك استخدام النموذج الذي تريده مثل text-davinci-003 أو gpt-4
        prompt=question,
        max_tokens=150
    )
    return response.choices[0].text.strip()

def main():
    welcome_message()
    while True:
        question = input("اسألني أي سؤال: ")
        if question.lower() in ["خروج", "انهاء", "quit", "exit"]:
            print("إلى اللقاء!")
            break
        answer = get_ai_response(question)
        print(f"الإجابة: {answer}")

if __name__ == "__main__":
    main()