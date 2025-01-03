# Loading Environment Variables from .env Files

For managing environment variables in a project, it’s common to use a `.env` file. Tools like `python-dotenv` make this process easier.

#### Example with `python-dotenv`:
1. Install the library:
   ```bash
   pip install python-dotenv
   ```

2. Create a `.env` file:
   ```
   DB_HOST=127.0.0.1
   API_KEY=abcd1234
   ```

3. Load and access the variables:
   ```python
   from dotenv import load_dotenv
   import os

   # Load the .env file
   load_dotenv()

   # Access variables
   db_host = os.getenv("DB_HOST", "default_env_value")
   api_key = os.getenv("API_KEY")

   print(f"Database Host: {db_host}")
   print(f"API Key: {api_key}")
   ```
