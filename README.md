     _           _                   _                                        _   
    | |         (_)                 (_)                                      | |  
  __| | ___  ___ _  __ _ _ __ ______ _ _ __  ___ _ __   ___ ______ __ _ _ __ | |_ 
 / _` |/ _ \/ __| |/ _` | '_ \______| | '_ \/ __| '_ \ / _ \______/ _` | '_ \| __|
| (_| |  __/\__ \ | (_| | | | |     | | | | \__ \ |_) | (_) |    | (_| | |_) | |_ 
 \__,_|\___||___/_|\__, |_| |_|     |_|_| |_|___/ .__/ \___/      \__, | .__/ \__|
                    __/ |                       | |                __/ | |        
                   |___/                        |_|               |___/|_|        
                   

This Django project implements a semantic search system that allows users to upload design screenshots and retrieve related design elements based on keywords. The system leverages OpenAI for generating embeddings and Pinecone for vector-based search. Additionally, the project supports automatic media file handling and environment configuration.

## Features

- **Semantic Search**: Upload design screenshots and retrieve relevant design elements using keyword-based searches.
- **Automatic Tagging**: Uses OpenAI to generate tags for uploaded images based on design elements.
- **Vector Search with Pinecone**: Embeds the generated tags and performs fast vector-based searches in Pinecone.
- **Media Handling**: Automatically handles and stores uploaded media, ensuring the files are excluded from version control.
- **Environment Configuration**: Secrets and environment variables are stored securely in `.env.local` and excluded from the repository.

## Requirements

- Python 3.x
- Django 3.x or higher
- OpenAI API Key
- Pinecone API Key
- A configured virtual environment (e.g., `venv`)

## Installation

1. **Clone the repository**:

   ```bash
   git clone https://github.com/yourusername/yourproject.git
   cd yourproject


2. **Create a virtual environment**:

   ```bash
   python3 -m venv venv
   source venv/bin/activate


3. **Install dependencies**:

   ```bash
   pip install -r requirements.txt


4. **Set up environment variables**:

   Create a .env.local file in the root of your project and add the following:

   DB_NAME=your_db_name
   DB_USER=your_db_user
   DB_PWD=your_db_password
   DB_PORT=your_db_port
   DB_HOST=your_db_host
SECRET_KEY=your_secret_key

   OPEN_AI_SECRETE_KEY=your_openai_api_key
   OPEN_AI_ORGANIZATION=your_openai_org_id
   PINECONE_API_KEY=your_pinecone_api_key


5. **Run database migrations**:

   ```bash
   python manage.py migrate
   ```

6. **Run the server**:

   ```bash
   python manage.py runserver
   ```


## Media Handling

Make sure the media/ directory and your .env.local file are ignored by Git. These are excluded in the .gitignore file.

.gitignore


# Ignore virtual environment
venv/

# Ignore media files
media/

# Ignore environment variables
.env.local


## Semantic Search Workflow

1. **Uploading Designs**: Users upload design screenshots through the `/upload` endpoint.
2. **Tag Generation**: OpenAI generates relevant tags for the uploaded images based on their design elements.
3. **Vector Embeddings**: The tags are converted into vector embeddings using OpenAI’s embedding API.
4. **Pinecone Search**: The vectors are stored in Pinecone, allowing fast, semantic-based searches through the `/search` endpoint.

## Using the Search Feature

To search for specific design elements (e.g., bentos, navbars, hero sections), simply enter the relevant keywords in the search bar on the `/search` page. The system will return all images tagged with relevant design elements based on semantic similarity.

## Removing Sensitive Files from Git

If you accidentally committed sensitive files like `.env.local` or media files, follow these steps to remove them:

1. **Remove files from Git tracking**:
   ```bash
   git rm --cached .env.local
   git rm -r --cached media
   ```

2. **Commit the changes**:
   ```bash
   git commit -m "Remove sensitive files from version control"
   git push origin <branch-name>
   ```

## License

This project is licensed under the MIT License.

Feel free to copy and paste this **README.md** into your project folder. It includes all the necessary details based on our previous conversation.