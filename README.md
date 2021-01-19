# ModMail
## Discord bot used to send anonymous messages to the moderators

### Setup

1. Create a discord bot
  - see https://discordpy.readthedocs.io/en/latest/discord.html for instructions
  
2. Install bot server software
### make sure you put your own secrets into the config files before you build the container

#### Please note that some versions of docker-compose may not work

```
[awol@gaming-amd ~]$ git clone https://github.com/NetworkChuckDiscord/Modmail.git && cd Modmail
[awol@gaming-amd ~]$ nano .mongoenv.sample # set the mongodb password here
[awol@gaming-amd ~]$ mv .mongoenv.sample .mongoenv
[awol@gaming-amd ~]$ nano .discordenv.sample # set your discord-token and use the same password as set earlier
[awol@gaming-amd ~]$ mv .discordenv.sample .mongoenv
[awol@gaming-amd ~]$ docker build . -t modmail
[awol@gaming-amd ~]$ docker compose up -d
```

## Usage

Once the bot is added to your server, you can interact by sending it a DM. When you do that the bot will create a channel in the catagory named tickets and anonymously forward the messages from that user into that channel. Any responses written in that channel will then be DMed to the user.

There are currently no commands for this bot hopefully there will be soon.

| permision | Command | Description |
|-----------|---------|-------------|
| Admin | &search [ticket-number] | Type is the search you want to use can be 1) -ltdate -etdate -author and term is the search term |
| Admin | &user_search [uid] | prints all tickets submitted by that user | 
| Admin | &mod_search [uid] | prints all tickets that the moderator has been involved | 
| Admin | &close | Archives the complaint putting a full log in admin log |
| User | &print | spits out all of the tickets sent by the user |

## Configuration

There is currently no config file that is still in the works:

| Setting | default Value | Description |
|---------|---------------|-------------|
| nods | false | Prevents Admins from running direct search due to security risk |
| prefex | $ | sets the default command prefex
| ticket_catagory | Null | catagory where the complaint channels are placed | 
| complaint_log | Null |log where archived messages go |
