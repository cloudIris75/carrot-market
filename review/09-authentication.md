# 09 Authentication

1. Send login info to back-end. (withHandler(), useMutation())  
   Search user info from back-end.
2. Issue token for user.
3. Sign in.

---

## Twilo

- SMS ← SID, TOKEN

## SendGrid

- Email ← KEY

---

## iron-session

- Encrypt the payload(token info). → O
- Use signed cookies. → O

## JWT(JSON Web Token)

- Encrypt the payload(token info). → X
- Use signed cookies. → O

---

## NextAuth

- Social Login Library
