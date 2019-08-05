# Problem
I would expect that [this link](https://svelte-spa-router-example.laughingbubba.now.sh/should-be-router404) would route to the `<NotFound/>` but it doesn't. [This does](https://svelte-spa-router-example.laughingbubba.now.sh/#/should-be-router404) because the hash-bang is already in the route.

# To Re-create Locally
Setup  
```
git clone https://github.com/LaughingBubba/svelte-spa-router-example.git
cd svelte-spa-router-example
npm i
```

### Run using sirv-cli
```
npm run dev
```
Then navigate to [http://localhost:5000/] and type should-be-router404 at the end of the URL and press enter. It just remains on the <Home/> route. 

If you go to [http://localhost:5000/#/should-be-router404] you'll get routed to the `<NotFound/>` componentn as expected.

### Run using serve
If you happen to have serve installed glabally:
```
serve ./public
```
This demonstrates the problem a little better as when you navigate to [http://localhost:5000/should-be-router404] you fall through to serve's own 404. 