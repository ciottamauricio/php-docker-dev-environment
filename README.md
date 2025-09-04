# Docker PHP Development Environment

A complete Docker Compose setup for PHP 8.2 development with Apache, GraphQL (Lighthouse), and Xdebug support.

## 🚀 Quick Start

1. **Clone this Docker environment:**
    
    ```
    git clone https://github.com/ciottamauricio/php-docker-dev-environment
    cd docker-php-environment    
    ```
    
2. **Add your projects:**
    
    ```
    # Clone your main project into the html folder
    git clone <https://github.com/yourusername/your-main-project.git> html
    
    # Clone your Laravel project into laravel12 folder (if needed)
    git clone <https://github.com/yourusername/your-laravel-project.git> laravel12    
    ```
    
3. **Start the environment:**
    
    ```
    docker compose up -d    
    ```
    
4. **Access your applications:**
    - Main project: `http://localhost` (or your configured port)
    - Laravel project: `http://localhost:8080` (adjust based on your config)

## 📁 Project Structure

```
docker-php/
├── apache-php/              # Apache and PHP configuration files
├── docker-compose.yml       # Main Docker Compose configuration
├── html/                   # 👈 Place your main project here (not tracked)
├── xdebug-profiler/        # Xdebug profiling output (auto-generated)
└── README.md              # This file
```

## 🛠️ What's Included

- **PHP 8.2** with Apache web server
- **GraphQL** support with Lighthouse framework
- **Database Support**: PostgreSQL and MySQL drivers
- **Xdebug**: Configured and ready for debugging
- **Composer**: Pre-installed for dependency management

## 🔧 Configuration

### Apache Configuration

- Custom Apache configs are in the `apache-php/` directory
- Virtual hosts and rewrites pre-configured

### Xdebug Setup

- **Port**: 9003 (configure your IDE accordingly)
- **Profiler output**: `xdebug-profiler/` directory
- Ready to use with PhpStorm, VS Code, or any Xdebug-compatible IDE

## 🚀 Usage Examples

```
# View container logs
docker compose logs -f

# Execute commands in the PHP container
docker compose exec web bash

# Install Composer dependencies
docker compose exec web composer install

# Run Laravel Artisan commands (if using Laravel)
docker compose exec web php artisan migrate
```

## 📋 Requirements

- [Docker](https://www.docker.com/get-started)
- [Docker Compose](https://docs.docker.com/compose/install/)
- Your project repositories

## 🎯 Development Workflow

1. Clone this repository
2. Add your project(s) to the appropriate folders (`html/`, `laravel12/`)
3. Start the containers with `docker compose up -d`
4. Develop in your IDE with full Xdebug support
5. Your changes are reflected immediately (volume mounted)

## 🔗 Related Projects

- [Your Main Project](https://github.com/yourusername/your-main-project)
- [Your Laravel Project](https://github.com/yourusername/your-laravel-project)

## 📝 Notes

- **Project Code**: This repository contains only the Docker environment setup
- **Application Code**: Your actual projects go in `html/` folders
- **Data Persistence**: Database data and logs are handled by Docker volumes
- **Hot Reload**: Changes in your code are immediately reflected in the containers
