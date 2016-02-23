# JSF Blog Sample

This sample has been prepared as a basic JavaServer Faces Blog. It is built in
NetBeans on GlassFish with MySQL.

The current version will work as-deployed within the Lambton College network and
the server IPRO is addressable, but to deploy this sample at home you will need
to set up a new database.

The following SQL is provided for reference:

    CREATE TABLE users (
        id INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
        username VARCHAR(255) NOT NULL UNIQUE,
        passhash VARCHAR(255) NOT NULL
    );
    
    CREATE TABLE posts (
        id INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
        user_id INT NOT NULL,
        title VARCHAR(255) NOT NULL UNIQUE,
        created_time DATETIME NOT NULL,
        contents TEXT,
        FOREIGN KEY posts(user_id) REFERENCES users(id)
    );
    
    -- Optional Sample Data
    -- Sets up 'user' with password 'P@ssw0rd'
    INSERT INTO users (username, passhash) 
        VALUES('user', 'E0478D09678A204E0DFD77C3F12500C08E03345E');
    
    INSERT INTO posts (user_id, title, created_time, contents)
        VALUES (1, 'Sample Post', NOW(), 'Lorem ipsum dolor sit amet.');