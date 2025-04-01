# MY CONCERNS!

Hey there – after a full week of tackling this project, I wanted to share a few thoughts on my process and the challenges I faced. Here’s a little insight into how I worked on it:
<br><br>
I kicked things off by breaking the project down into its core assumptions and pinpointing potential issues, risks, and the tests that needed to be in place. The initial focus was on the architecture. The task demanded an independent database – one that could easily be swapped for a different source or format in the future. Out of all the popular architectural patterns, I chose one with the most independent layers (think Onion Architecture). It was a no-brainer: centralise the business model (the domain) and separate all logic as much as possible.
<br><br>
Then there was the database. Because the connection was a bit unstable, I needed a solution that wouldn’t let it become a show-stopper. The idea was to set up the database once and then update it asynchronously – effectively swapping one in-memory Trie for another when new data arrives. It’s super quick and doesn’t interrupt the user experience.
<br><br>
Next up was input handling. The touch panel doesn’t allow special characters, so I built a function called **CleanName**. It not only strips out any special characters that the user couldn’t possibly enter but also converts them into spaces where necessary. This ensures that the data shown is exactly what the user can type, and it’s also a neat way to protect against SQL injection, XSS, and other nasty surprises. The motto? Never Trust User Inputs!
<br><br>
Lastly, updates are handled in the background. Every 12 hours (or however you fancy it), a service fetches the latest station data, builds a new Trie, and if it finds any differences from the current one – it swaps them out in a flash. This means the API is always running with up-to-date data without any downtime.
<br><br>
On the testing side, I went with xUnit – it just gets well with .NET and integrates nicely with CI/CD. It’s modern, straightforward, and has excellent support for dependency injection and parallel testing. Alternatives like NUnit or MSTest were considered, but xUnit just felt right for this project.
<br><br>

I had big plans to lock down sensitive data in Program.cs. My idea was to use AES encryption with Base64 decryption and securely store the secret key in Docker Swarm (mounted at /run/secrets/my_secret_key). Unfortunately, I ran headfirst into a maze of configuration issues—especially around passing the environment variable during the build. With deadlines breathing down my neck, I decided it was best to focus on delivering a rock-solid, functional API rather than getting stuck in the containerisation rabbit hole.
<br><br>
Am not super satisfied of it, because I was really excited to show off that security solution, but sometimes you just have to prioritise what works best in the time you have. In the end, I’m happy with the API and all that I learned along the way – even if it wasn’t perfect :P
<br><br>
In short, I’ve taken an approach that balances simplicity, efficiency, and security. I truly enjoyed the challenge, learned a ton, and even though I hit a few bumps (especially around containerisation and secure key handling), it was all part of the learning curve. Thanks for the opportunity – it’s been a brilliant ride!
<br><br>
Best regards,  
**Mariusz Janowiak**