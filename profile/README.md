## Hi there 👋
This is a twitter clone with minimal functionalities.
We will add features slowly.

Setting up the docker instances

sudo docker compose up -d

sudo docker exec -t auth-postgres psql -U authuser -d auth_db
CREATE TABLE users (
  id SERIAL PRIMARY KEY,
  username VARCHAR(50) UNIQUE NOT NULL,
  password VARCHAR(100) NOT NULL
);

sudo docker exec -t user-management-postgres psql -U usermgmtuser -d user_management_db
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    username VARCHAR(255) NOT NULL UNIQUE,
    first_name VARCHAR(255) NOT NULL,
    last_name VARCHAR(255),
    email VARCHAR(255) NOT NULL UNIQUE 
);

sudo docker exec -it cassandra cqlsh
CREATE KEYSPACE tweets_keyspace WITH REPLICATION = { 'class' : 'SimpleStrategy', 'replication_factor' : 1 };
USE twitter_clone;
CREATE TABLE tweet (
    id UUID PRIMARY KEY,
    user_id UUID,
    content TEXT,
    media_links LIST<TEXT>,
    created_at TIMESTAMP
);

<!--

**Here are some ideas to get you started:**

🙋‍♀️ A short introduction - what is your organization all about?
🌈 Contribution guidelines - how can the community get involved?
👩‍💻 Useful resources - where can the community find your docs? Is there anything else the community should know?
🍿 Fun facts - what does your team eat for breakfast?
🧙 Remember, you can do mighty things with the power of [Markdown](https://docs.github.com/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
-->
