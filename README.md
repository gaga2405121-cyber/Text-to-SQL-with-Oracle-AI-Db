# 🤖 Text-to-SQL-with-Oracle-AI-Db - Convert plain English into database queries

[![](https://img.shields.io/badge/Download-Project-blue.svg)](https://github.com/gaga2405121-cyber/Text-to-SQL-with-Oracle-AI-Db)

This project helps you turn simple questions into complex database instructions. You do not need to write code to get answers from your information. It uses the Oracle AI Database 26ai features to process natural language.

## 📋 What This Tool Does

Computers usually require specific code to fetch data. This tool removes that barrier. You type a question, and the software creates the query for you. It uses four distinct methods to handle your requests:

* Standard Execution: This mode runs your question directly against the database and provides the result.
* SHOWSQL: This mode reveals the underlying code so you can learn how the query works.
* NARRATE: This mode provides detailed insights and context about the data you requested.
* CHAT: This mode holds a conversation to refine your results over several steps.

## 🛠 Prerequisites

You need a computer running Windows 10 or Windows 11. You also need a connection to an Oracle Database that includes the Select AI feature. Ensure you have the following items ready:

* A stable internet connection.
* A web browser like Chrome, Edge, or Firefox.
* An active connection string for your Oracle Database.
* Access to a Jupyter notebook environment.

Your computer should have at least 8GB of RAM to run these processes smoothly.

## 📥 How to Get Started

You must visit the project page to access the files. The software requires a browser-based notebook viewer to function correctly on your machine.

[Visit the repository to download this project](https://github.com/gaga2405121-cyber/Text-to-SQL-with-Oracle-AI-Db)

1. Navigate to the link provided above.
2. Look for the green button labeled "Code".
3. Click "Download ZIP" to save the project files to your computer.
4. Extract the contents of the ZIP folder to a known location, such as your Desktop or Documents folder.

## ⚙️ Setting Up Your Environment

This project runs inside a tool called Jupyter. You do not need to install complex software, but you must have a way to view the notebook files.

1. Install Anaconda or a similar Python environment manager from the official website.
2. Open the application and select "Jupyter Notebook" from the list of programs.
3. Use the file explorer window inside your browser to find the folder where you extracted the project.
4. Open the file ending with the extension .ipynb.

## 🔑 Configuring Your Database Connection

The notebook needs your database details to fetch information. You will see a block of text at the top of the notebook with placeholders for your information.

* Find the line labeled "Database User". Type your username between the quotation marks.
* Find the line labeled "Password". Type your secure password there.
* Find the "Connection String" line. Insert the address of your Oracle instance here.

Do not share this file with others after you add your login details.

## 🚀 Running Your First Query

Once your details are entered, you can start asking questions. Each section of the notebook contains a cell for input.

1. Click inside the cell that says "Input your question here".
2. Type your question in plain English. For example, "Show me the top five employees by salary."
3. Press the "Play" or "Run" button at the top of the screen.
4. Wait for the system to process the request. The results will appear directly below the cell.

If you encounter an error, check that your internet connection is active and your database credentials are correct.

## 🔍 Understanding the Modes

Each mode serves a different purpose. If you want a quick answer, use the standard execution mode. If you are learning how SQL works, use the SHOWSQL mode to see the translation happening in real time. 

The NARRATE mode helps if you need a summary of the data rather than a raw table. Use the CHAT mode if you have a complex request that requires multiple back-and-forth steps to clarify the data you need.

## 💻 Managing System Resources

Processing natural language takes effort from your computer. If the notebook feels slow, close other programs like your web browser tabs or desktop applications. Ensure your database connection stays active during the process. If you lose the connection, simply restart the notebook cell to reconnect.

## 🛡 Security and Privacy

Your questions are processed by the Oracle AI engine. Do not type sensitive data or personal information into the input fields. The tool is designed to work with generic database records. If you work in a corporate environment, consult your database administrator to ensure you follow your company policies regarding external AI tools.

## 🔧 Resolving Common Issues

* The notebook does not load: Ensure you have opened the file inside the Jupyter environment, not just by double-clicking the file in Windows.
* Connection refused: Check your database connection string for typos. Verify that your database is online and accepting connections.
* No data returned: Check that the table names in your database match the generic examples used in the notebook. You may need to edit the SQL table references to match your specific layout.
* Slow response times: Large datasets require more time to process. Start with simple questions to ensure your connection works before asking complex queries.

## 📚 Learning More

You can explore the settings to change how the AI interprets your words. The configuration section allows you to choose different models for processing. Depending on your subscription, you might choose models that prioritize speed over detailed analysis. Review the documentation provided by your Oracle account representative to see which models you can access. 

This environment provides a template for data science tasks. You can duplicate the notebook to create new versions for different departments in your organization. Keep one original copy as a backup and edit the others as needed for your specific reporting needs.