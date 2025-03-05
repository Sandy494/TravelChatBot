# TravelChatBot

**Objectives** Travel Chat Bot: Travel chat bot is an application built using openAI API to interact with the users and fetch details for their travel plan like: Travel_From, Travel_To, Travel_Mode, and Class. 
**Data** A synthetic data containing 1000 records was created using chatGPT prompt to have above fields along with Price.( Please find the csv file )
The cities under scope of this application are: 
o	'Bangalore',
o	'Goa',
o	'Hyderabad',
o	'Delhi',
o	'Pune',
o	'Mumbai',
o	'Kolkata',
o	'Chennai',
o	'Jaipur',
o	'Ahmedabad'
The Mode of Travel under scope of this application are: 
o	‘Bus’, 
o	’Flight’ &
o	‘Train’
Class applicable as per the Mode of Travel are:
o	Bus: AC, Non AC, Sleeper
o	Train: First Class, AC2 Tier, AC3 Tier, Sleeper
o	Flight: Business, Economy

A Travel chat bot enables the user to interact with openAI APIs to capture the useful details in the form of a python dictionary which is then matched against the data present in the csv file to display in tabular format the travel details to the users.

** Function Details**
a. initialize_conversation ()
•	Initializes the chatbot with a system message explaining how the user should provide travel details.
•	Returns a conversation history list with the system message.
b. dictionary_present(response)
•	Extracts structured travel details (Travel_From, Travel_To, Travel_Mode, Class) from user input.
•	Uses OpenAI's GPT to parse the response and return it in JSON format.
•	If parsing fails, it returns an empty dictionary.
c. moderation_check (user_input)
•	Uses OpenAI’s Moderation API to check if the input contains inappropriate content.
•	Returns "Flagged" if the content is inappropriate, otherwise returns "Not Flagged".
d. get_chat_completions (conversation, json_format=True)
•	Calls OpenAI's GPT model to generate a chatbot response.
•	Uses a conversation history as input and returns a formatted response.
e. intent_confirmation_layer (travel_details, conversation)
•	Checks if all required details (Travel_From, Travel_To, Travel_Mode, and Class) are present.
•	If details are missing, prompts the user for clarification.
•	Returns a confirmation result: "Yes" if all details are present, otherwise "No" with a clarification request.
f. find_matching_travel_options(travel_details, csv_file)
•	Reads a CSV file containing travel options.
•	Matches rows that have the same Travel_From, Travel_To, and Travel_Mode as extracted from the user input.
•	If a match is found, returns a formatted table of travel options using the tabulate library.

g. main()
•	Runs the chatbot loop:
1.	Welcomes the user and initializes the conversation.
2.	Waits for user input.
3.	If the user enters "exit" or "bye", the chatbot terminates.
4.	Checks if the input is flagged by the moderation system.
5.	Extracts structured travel details.
6.	If details are missing, asks for clarification.
7.	Once all details are present, records the travel information.
8.	Retrieves matching travel options from the CSV file and displays them in a tabular format.





** Flow of Events**
1.	User Input: The user provides their travel details in natural language.
2.	Moderation Check: Ensures that the input is appropriate.
3.	Extract Travel Details: The chatbot processes the input and extracts details like source, destination, mode, and class.
4.	Confirm Missing Details: If any details are missing, the chatbot asks for clarification.
5.	Find Matching Travel Options: Once details are confirmed, the chatbot searches the CSV file for available travel options.
6.	Display Results: The chatbot presents the best-matching travel options in a table.
7.	Repeat or Exit: The user can enter another query or exit the chatbot.
