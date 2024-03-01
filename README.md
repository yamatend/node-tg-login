# node-telegram-login

```
npm install node-tg-login
```

Simply use the check method

```typescript
import { TelegramLogin } from 'node-tg-login'
const TelegramAuth = new TelegramLogin('<BOT_TOKEN>');

const verify = (data: TelegramLoginPayload) => 
  console.log(
    TelegramAuth.checkLoginData(data) ?
    `Payload is safe! We can trust ${data.first_name}`,
    'Uhm. Payload is not secure'
  );
```

Or as an express.js middleware like this:

```typescript
import { TelegramLogin } from 'node-tg-login'
const TelegramAuth = new TelegramLogin('<BOT_TOKEN>');

app.get('/login/telegram', TelegramAuth.defaultMiddleware(), (req, res) => {
  console.log(res.locals.telegram_user)
});

