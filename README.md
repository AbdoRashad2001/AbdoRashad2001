import requests

import json

import sys



# Replace with your actual API key

API_KEY = "AIzaSyB3ah_uPm4NSw6GFh4liS4P7E9KmTM_6Hk"



text = ""

if len(sys.argv) > 1:

  text = 'Help with any question i ask about linux bash commands only. other wise if my question is off topic please only say : "I Can not assist with any thing further more linux or bash commands help. sorry but i am limited" So my questions is : " '+sys.argv[1]

else :

  exit()



# Content to send in the request

content = {

  "contents": [

    {

      "parts": [

        {

          "text":text

        }

      ]

    }

  ]

}



# Endpoint URL

url = "https://generativelanguage.googleapis.com/v1beta/models/gemini-pro:generateContent?key="+ API_KEY



# Set headers

headers = {"Content-Type": "application/json"}



# Send POST request

response = requests.post(url, headers=headers, json=content)



# Handle response

if response.status_code == 200:

 # Parse JSON response

 data = response.json().get('candidates')[0].get('content').get('parts')[0].get('text')

 # Access generated text

 print(data)

else:

  print("Error:",response.status_code, response.text)
