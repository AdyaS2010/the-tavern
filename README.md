# The Tavern

Welcome to The Tavern, your friendly quest bot! I run in the bag channels in Hackclub's [#market](https://app.slack.com/client/T0266FRGM/C06GA0PSXC5) channel! Just ping [@The Tavern](https://app.slack.com/client/T0266FRGM/D07HGJZG6HJ) and you will be on your way to fame and glory!

## Creating New Quests

You can easily create new quests by editing the YAML file `/lib/quests.yaml`. Here’s a simple example of how a quest might look:

```yaml
quests:
  baby-bear:
    description: 'A baby bear has lost its mother in the forest. Help the baby bear find its mother and return to The Tavern for a reward.'
    items: 'Stew, Bread'
    scenes:
      scene1:
        prompt: 'Agree to help the baby bear find its mom.'
        character: 'cubby'
      scene2:
        prompt: 'Explore the forest with the bear and find a squirrel for help.'
        character: 'cubby'
```

characters can be created in the same file by making a new entry like this:

```yaml
characters:
    cubby:
        prompt: "You are a curious and innocent baby bear. You trust the party quickly and follow them closely, but you often get distracted by smells or sounds. You mostly communicate through gestures, growls, and occasional babyish words like 'Mama.' Your goal is to find your mother."
        image: 'https://cloud-e3njarhaf-hack-club-bot.vercel.app/3baby.jpg'
```

Just customize the prompts and characters, and The Tavern bot will auto source everything and work!

## Development

### Getting it up and running

TODO

### Editing Quests

If you need to change the quest structure or add new characters, simply edit the relevant YAML files and restart The Tavern bot.

```bash
git pull
systemctl --user restart tavern
```

This way, your new quests will be ready for action!

## Production

Deploying The Tavern in a production environment is easy. Simply use a systemctl service file to manage the bot (i totaly would have used docker but i was burned by docker-prisma interactions in the past and so now I'm sticking to systemd services lol):

```ini
[Unit]
Description=The Tavern Bot
DefaultDependencies=no
After=network-online.target

[Service]
Type=exec
WorkingDirectory=/home/kierank/tavern
ExecStart=python run.py
TimeoutStartSec=0
Restart=on-failure
RestartSec=1s

[Install]
WantedBy=default.target
```

---

_© 2024 Kieran Klukas_  
_Licensed under [AGPL 3.0](LICENSE.md)_

---