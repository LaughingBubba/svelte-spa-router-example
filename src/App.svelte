<script>

import { Router, Route, navigateTo } from 'svero'

import Home from './routes/Home.svelte'
import Name from './routes/Name.svelte'
import Wild from './routes/Wild.svelte'
import Regex from './routes/Regex.svelte'
import About from './routes/About.svelte'
import NotFound from './routes/NotFound.svelte'

</script>
<style>
/* Style for "active" links; need to mark this :global because the router adds the class directly */
:global(a.active) {
    color: crimson;
}
</style>


<h1>svelte-spa-router example</h1>
<!-- Navigation links, using the "link" action -->
<!-- Also, use the "active" action to add the "active" CSS class when the URL matches -->
<ul class="navigation-links">
    <li><a href="/">Home</a></li>
    <li><a href="/about"><b>About</b></a></li>
    <li><a href="/hello/svelte/joe">Say hi!</a></li>
    <li><a href="/does/not/exist">Not found</a></li>
</ul>

<!-- Navigate with buttons -->
<p class="navigation-buttons">
    <button on:click={() => navigateTo('/wild/something')}>Visit /wild/something</button>
    <button on:click={() => window.history.back()}>Go back</button>
    <button on:click={() => navigateTo('/wild/replaced')}>Replace current page</button>
</p>

<!-- Show the router -->

<Router>
    <Route path="*" component={NotFound} />
    <Route exact path="/" component={Home} />
    <Route path="/about" component={About} />
    <Route path="/hello/svelte/:first/:last" component={Name} />
    <Route path="/about/:who/123/:where" component={Name} />
    <Route path="/static">
        <h1>It works!</h1>
    </Route>
</Router>
