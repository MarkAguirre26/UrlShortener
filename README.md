# URL Shortener with Spring Boot
This is a simple URL shortener application built using Spring Boot. The application allows you to shorten long URLs, store them in memory, and then redirect users to the original URL when they visit the shortened link.

### Features
Shorten URLs by providing a long URL.
Retrieve the original URL from the shortened one.
Base URL is configurable via application.properties.
In-memory storage for URL mappings.
### Prerequisites
Java 11+ (or the latest version of JDK)
Maven (for building the project)
Spring Boot (for the framework)
Setup
### 1. Clone the repository
Clone the project to your local machine using the following command:

```bash
git clone https://github.com/your-username/url-shortener.git
```

### 2. Build the project
Navigate to the project directory and build the project using Maven:

```bash
cd url-shortener
mvn clean install
```

### 3. Configure the application properties
In `src/main/resources/application.properties`, configure the `base.url` property. This will define the base URL for all shortened URLs.

```properties
base.url=http://localhost:8080/
```

You can modify this to use any custom URL (e.g., a production URL) later.

### 4. Run the application
To run the Spring Boot application, use the following command:

```bash
mvn spring-boot:run
```

Your application will start on `http://localhost:8080/` by default.

### 5. Test the endpoints

#### Shorten a URL
To shorten a URL, send a POST request with a parameter `originalUrl`:

```bash
curl -X POST "http://localhost:8080/url/shorten?originalUrl=https://www.example.com"
```

The response will be a shortened URL:

```bash
http://localhost:8080/abcd12
```

#### Redirect to the original URL
To get redirected to the original URL, visit the shortened URL in your browser:

```bash
http://localhost:8080/abcd12
```

You will be redirected to `https://www.example.com`.

## How It Works

- **Shortening URLs**: The `UrlService` generates a random alphanumeric string to create the shortened URL. This string is mapped to the original URL in an in-memory `Map`.
- **Redirecting to Original URL**: When a user visits the shortened URL, the application looks up the original URL in the `Map` and redirects the user to it.

## Customizing the Application

- **Change the base URL**: Modify the `base.url` property in `application.properties` to change the base URL used for shortened links.
- **Persist URLs**: This version stores URLs in memory. For persistence, you can integrate a database like MySQL or MongoDB.

## Running in Production
For running this application in production, consider:

- Deploying it behind a reverse proxy (e.g., Nginx).
- Configuring HTTPS for secure communication.
- Integrating a persistent storage solution (database) for better scalability and reliability.

## License
This project is licensed under the MIT License - see the LICENSE file for details.

## Contributing

1. Fork the repository.
2. Create a new branch (`git checkout -b feature-branch`).
3. Make your changes.
4. Commit your changes (`git commit -am 'Add new feature'`).
5. Push to the branch (`git push origin feature-branch`).
6. Create a new Pull Request.

## ToDo
1. Add a database to store the URLs
2. Short and meaningful domain name
   
```
