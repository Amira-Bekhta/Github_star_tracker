<h1>Github star tracker 🌟</h1>

<h3>Hello everyone, here is my latest project, and maybe the only frontend project here in my Github! This is a Github star tracking app that I have made to track the count of Github stars for the <a href="https://github.com/docuglean-ai/docuglean">Docuglean SDK repository</a> 🚀</h3>
<h3>Find the app <a href="https://amira-bekhta.github.io/Github_star_tracker/">here</a></h3>

<h1>Highlights 🪄</h1>
<h2>1- Progress bar styling 🎨</h2>
<p>When you use the HTML progress tag, it might be a bit tricky to style the progress bar in CSS, here is how I did it:</p> <br>

```
  #progress {
            width: 90%;
            max-width: 30em; 
            height: 2em;
            -webkit-appearance: none;
            -moz-appearance: none;    
            appearance: none;     
}

        #progress::-webkit-progress-bar {
            background-color: azure; 
            border: 0.06em solid rgb(180, 180, 180);
 }

        #progress::-webkit-progress-value {
            background-color: gold; 
            transition: width 0.3s ease-in-out; 
 }
```

<h2>2- Using the Github API 🔎</h2>

<p>At first, I thought using Github API is the hardest part, however I discovered how easy it is to retrieve the star count of any Github repository using the API:</p> <br>

```
<script>
        async function updateStars() {
            try {
                const response = await fetch('https://api.github.com/repos/docuglean-ai/docuglean');
                const data = await response.json();
                const stars = data.stargazers_count;
                document.getElementById('progress').value = stars;
                document.querySelector('h3').textContent = `${stars} stars so far!`;
            } catch (error) {
                console.error('Failed to fetch star count:', error);
                document.querySelector('h3').textContent = 'Unable to load stars 😢';
            }
        }
        setInterval(updateStars, 60000); 

        updateStars();
</script>
```
