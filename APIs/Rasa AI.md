Website: [Rasa](https://rasa.com)

Note – it wouldn't run on my MacBook Air as the version of TensorFlow used in the project [doesn't support M1 chips](https://stackoverflow.com/questions/65279266/rasa-m1-macbook-pro). I ended up using a Digital Ocean instance (the $20 one with 4GB of RAM).

- [API endpoint & response schema](https://rasa.com/docs/rasa/connectors/your-own-website)

## Commands

Train the model:
```bash
rasa train
```

Run a server with CORS:
```bash
rasa run -m models --enable-api --cors "*" --debug
```

