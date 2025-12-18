# Grid Quest - Multiplayer Adventure Game

A multiplayer, grid-based adventure game built with Ruby on Rails as the final project for the Software Engineering Languages and Tools (SELT) course.

## Overview

Grid Quest is an interactive, multiplayer web-based game where players can explore grid-based worlds, complete quests, collect items, play mini-games, and interact with friends. Players earn XP, level up, and customize their experience through various power-ups and items.

## Key Features

### World Management
- **Create Custom Worlds**: Build your own grid-based worlds with customizable sizes and settings
- **Public & Private Worlds**: Control who can join your world
- **World Invitations**: Invite friends to join your private worlds
- **Multi-World Support**: Join and play in multiple worlds simultaneously

### Social Features
- **Friend System**: Add friends, send/receive friend requests, and approve connections
- **Real-time Chat**: Message other players in the same world
- **Friend Invites**: Invite friends to worlds you've created

### Gameplay
- **Grid-Based Movement**: Navigate through worlds on a grid system
- **Quest System**:  Complete dynamically generated quests and trivia challenges using OpenAI integration
- **Mini-Games**: Play Blackjack to earn or wager credits
- **Shop System**: Purchase items and power-ups
- **Inventory Management**: Collect and use items that affect gameplay
- **XP & Leveling**: Gain experience and level up your character

### Premium Features
- **Plus Membership**: Unlock additional features and benefits
- **Credit System**: Earn and spend in-game credits
- **Power-ups**:  
  - XP Boost:  Increase experience gain
  - Speed Boost: Move faster across the grid
  - Luck Boost:  Improve chances in random events

### User Management
- **Secure Authentication**: Email-based registration with BCrypt password hashing
- **Session Management**:  Secure session tokens
- **Password Reset**: Email-based password recovery via SendGrid
- **Profile Customization**: Unique display names and profile settings

## Tech Stack

### Backend
- **Framework**: Ruby on Rails 7.1
- **Ruby Version**:  3.0.7
- **Database**: PostgreSQL with pgcrypto extension
- **Job Queue**: GoodJob for background processing
- **File Storage**: Active Storage with AWS S3 (production)

### Frontend
- **JavaScript**:  jQuery, Turbolinks, CoffeeScript
- **CSS**:  Sass/SCSS
- **Asset Pipeline**: Terser, Uglifier

### Testing
- **Unit Testing**: RSpec
- **Integration Testing**: Cucumber with Capybara
- **Code Coverage**:  SimpleCov
- **Linting**: RuboCop with Rails, RSpec, and Capybara extensions

### Third-Party Integrations
- **Email**: SendGrid for transactional emails
- **AI**: OpenAI API for quest generation
- **Currency**: Money gem with Open Exchange Rates
- **Payment Validation**: Credit card detector

## Prerequisites

- Ruby 3.0.7
- PostgreSQL 12+
- Node.js and Yarn (for asset compilation)
- Redis (optional, for GoodJob)

## Getting Started

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/NikHerdt/projectdirectory-selt_2024_team_002.git
   cd projectdirectory-selt_2024_team_002
   ```

2. **Install dependencies**
   ```bash
   bundle install
   ```

3. **Set up environment variables**
   
   Create a `.env` file in the root directory with the following: 
   ```env
   SENDGRID_API_KEY=your_sendgrid_api_key
   OPENAI_API_KEY=your_openai_api_key
   OPEN_EXCHANGE_RATES_APP_ID=your_exchange_rates_app_id
   DATABASE_URL=your_database_url
   ```

4. **Set up the database**
   ```bash
   rails db:create
   rails db:migrate
   rails db: seed
   ```

5. **Start the application**
   ```bash
   rails server
   ```
   
   Or use Foreman to start all services:
   ```bash
   foreman start
   ```

6. **Visit the application**
   
   Open your browser to `http://localhost:3000`

## Running Tests

### RSpec (Unit Tests)
```bash
bundle exec rspec
```

### Cucumber (Feature Tests)
```bash
bundle exec cucumber
```

### RuboCop (Code Linting)
```bash
bundle exec rubocop
```

### Code Coverage
After running tests, view coverage report:
```bash
open coverage/index.html
```

## Project Structure

```
.
├── app/
│   ├── controllers/     # Application controllers
│   ├── models/          # ActiveRecord models
│   ├── views/           # View templates
│   ├── helpers/         # View helpers
│   ├── jobs/            # Background jobs
│   ├── mailers/         # Email mailers
│   └── assets/          # Stylesheets, JavaScripts, images
├── config/              # Application configuration
├── db/                  # Database migrations and schema
├── features/            # Cucumber feature files
├── spec/                # RSpec test files
├── public/              # Static files
└── vendor/              # Third-party code
```

## How to Play

1. **Register/Login**: Create an account or log in with existing credentials
2. **Create or Join a World**: Start your own world or join an existing one
3. **Explore**: Use the grid interface to move your character around the world
4. **Complete Quests**: Encounter and complete quests to earn XP and credits
5. **Shop & Inventory**: Purchase items and use them to enhance your gameplay
6. **Play Mini-Games**: Try your luck at Blackjack to earn more credits
7. **Add Friends**: Build your network and invite friends to your worlds
8. **Chat**: Communicate with other players in real-time

## Database Models

- **User**: Player accounts with authentication
- **World**: Game worlds with grid configurations
- **UserWorld**: Join table tracking player progress in each world
- **Gridsquare**:  Individual cells in the world grid
- **Quest**: Dynamically generated quests and trivia
- **Item/InventoryItem**: Items and player inventories
- **Shop/ShopsItem**: In-game shops and their inventories
- **Message**: Chat messages between players
- **Friendship**: Friend relationships and requests
- **BlackjackGame**:  Blackjack game state
- **OpenaiEvent**: AI-generated events

## Security Features

- BCrypt password hashing
- Secure session tokens
- Email validation with DNS verification
- CSRF protection
- SQL injection prevention through ActiveRecord

## Deployment

The application is configured for deployment on Heroku: 

- Procfile included for web and worker processes
- Production gems: `rails_12factor`, `aws-sdk-s3`
- GoodJob for background job processing
- PostgreSQL database

### Deploy to Heroku

```bash
heroku create your-app-name
heroku addons: create heroku-postgresql
heroku config:set SENDGRID_API_KEY=your_key
heroku config:set OPENAI_API_KEY=your_key
heroku config:set OPEN_EXCHANGE_RATES_APP_ID=your_id
git push heroku main
heroku run rails db:migrate
```

## Contributing

This is a course project.  For team members:

1. Create a feature branch
2. Make your changes
3. Run tests and linting
4. Submit a pull request

## License

This project was created as coursework for the Software Engineering Languages and Tools course. 

## Team

SELT 2024 - Team 002
