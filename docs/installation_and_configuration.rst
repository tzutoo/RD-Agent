==============================
Installation and Configuration
==============================

Installation
============

**Install RDAgent**: For different scenarios

- for purely users: please use ``pip install rdagent`` to install RDAgent
- for dev users: `See development <development.html>`_

**Install Docker**: RDAgent is designed for research and development, acting like a human researcher and developer. It can write and run code in various environments, primarily using Docker for code execution. This keeps the remaining dependencies simple. Users must ensure Docker is installed before attempting most scenarios. Please refer to the `official 🐳Docker page <https://docs.docker.com/engine/install/>`_ for installation instructions.

Configuration
=============

To run the application, please create a `.env` file in the root directory of the project and add environment variables according to your requirements.

The standard configuration options for the user using the OpenAI API are provided in the `.env.example` file.

Here are some other configuration options that you can use:

OpenAI API
------------

Here is a standard configuration for the user using the OpenAI API.

   .. code-block:: Properties

      OPENAI_API_KEY=<your_api_key>
      EMBEDDING_MODEL=text-embedding-3-small
      CHAT_MODEL=gpt-4-turbo

Configuration List

------------------

.. TODO: use `autodoc-pydantic` .

- OpenAI API Setting

+-----------------------------------+-----------------------------------------------------------------+-------------------------+
| Configuration Option              | Meaning                                                         | Default Value           |
+===================================+=================================================================+=========================+
| OPENAI_API_KEY                    | API key for both chat and embedding models                      | None                    |
+-----------------------------------+-----------------------------------------------------------------+-------------------------+
| EMBEDDING_OPENAI_API_KEY          | Use a different API key for embedding model                     | None                    |
+-----------------------------------+-----------------------------------------------------------------+-------------------------+
| CHAT_OPENAI_API_KEY               | Set to use a different API key for chat model                   | None                    |
+-----------------------------------+-----------------------------------------------------------------+-------------------------+
| EMBEDDING_MODEL                   | Name of the embedding model                                     | text-embedding-3-small  |
+-----------------------------------+-----------------------------------------------------------------+-------------------------+
| CHAT_MODEL                        | Name of the chat model                                          | gpt-4-turbo             |
+-----------------------------------+-----------------------------------------------------------------+-------------------------+


- Globol Setting

+-----------------------------+--------------------------------------------------+-------------------------+
| Configuration Option        | Meaning                                          | Default Value           |
+=============================+==================================================+=========================+
| max_retry                   | Maximum number of times to retry                 | 10                      |
+-----------------------------+--------------------------------------------------+-------------------------+
| retry_wait_seconds          | Number of seconds to wait before retrying        | 1                       |
+-----------------------------+--------------------------------------------------+-------------------------+
+ log_trace_path              | Path to log trace file                           | None                    |
+-----------------------------+--------------------------------------------------+-------------------------+
+ log_llm_chat_content        | Flag to indicate if chat content is logged       | True                    |
+-----------------------------+--------------------------------------------------+-------------------------+


- Cache Setting

.. TODO: update Meaning for caches

+------------------------------+--------------------------------------------------+-------------------------+
| Configuration Option         | Meaning                                          | Default Value           |
+==============================+==================================================+=========================+
| dump_chat_cache              | Flag to indicate if chat cache is dumped         | False                   |
+------------------------------+--------------------------------------------------+-------------------------+
| dump_embedding_cache         | Flag to indicate if embedding cache is dumped    | False                   |
+------------------------------+--------------------------------------------------+-------------------------+
| use_chat_cache               | Flag to indicate if chat cache is used           | False                   |
+------------------------------+--------------------------------------------------+-------------------------+
| use_embedding_cache          | Flag to indicate if embedding cache is used      | False                   |
+------------------------------+--------------------------------------------------+-------------------------+
| prompt_cache_path            | Path to prompt cache                             | ./prompt_cache.db       |
+------------------------------+--------------------------------------------------+-------------------------+
| max_past_message_include     | Maximum number of past messages to include       | 10                      |
+------------------------------+--------------------------------------------------+-------------------------+




Loading Configuration
---------------------

For users' convenience, we provide a CLI interface called `rdagent`, which automatically runs `load_dotenv()` to load environment variables from the `.env` file.
However, this feature is not enabled by default for other scripts. We recommend users load the environment with the following steps:


- ⚙️ Environment Configuration
    - Place the `.env` file in the same directory as the `.env.example` file.
        - The `.env.example` file contains the environment variables required for users using the OpenAI API (Please note that `.env.example` is an example file. `.env` is the one that will be finally used.)

    - Export each variable in the .env file:

      .. code-block:: sh

          export $(grep -v '^#' .env | xargs)
    
    - If you want to change the default environment variables, you can refer to the above configuration and edith the `.env` file.

