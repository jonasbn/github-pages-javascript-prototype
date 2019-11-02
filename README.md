
# GitHub Pages JavaScript Prototype

_- Experimenting with GitHub Pages and JavaScript_

## Introduction

This experiment and prototype project was triggered with the question:

> Can you host semi-interactive pages with data using [GitHub Pages][github_pages]?

I have [blogged][last_mover] about using [GitHub Pages][github_pages] previously, but simply for generating a webpage based on rendering of Markdown formatted content.

I know it is possible to alter the standard themes using [Sass], but I have not gotten into more dynamic solutions, since I got my first itch scratched (see the mentioned [blog post][last_mover]).

I am sure it would be quite easy, that it would be possible to add additional JavaScript so the more interesting part of the question is related to the _data_.

Now it is time to dig into the process.

## Process

I am by no means a frontend developer and and my JavaScript it _pretty_ since it was primarily pre-jQuery and early jQuery. I am experimenting a bit with [Vue] on the side and I did a [React] tutorial and [Svelte] is on my list of technologies to evaluate.

1. I _googled_  a bit and found a blog post entitled ["Using GitHub Pages To Host Your Website"][treehouse_blog], after reading this and it supported my own experience I was confident I could accomplish something

2. I went to [Codepen.io] and found a beautiful _pen_ called ["Terminal Text Effect"][terminal_text_effect], do check it out. This _pen_ holds HTML, CSS and JavaScript, so I have all the building blocks I need

3. Next up was embedding the pieces from the _pen_ in an HTML page. So I downloaded [a basic HTML5 skeleton file][basic_html5_skeleton_file] and got everything working locally

4. I enabled [GitHub Pages][github_pages] for [my newly created GitHub repository][github-pages-javascript-prototype] and uploaded everything. The implementation became available at:

    `https://jonasbn.github.io/github-pages-javascript-prototype/`

    Instead of:

    `https://github.com/jonasbn/github-pages-javascript-prototype`

    Where you can just see the files

    Do note that the above thing took me some time, because I forgot this step could not understand, why things where not working. One small bump in the road, but nothing compared to the next steps

5. Now I wanted to alter ["Terminal Text Effect"][terminal_text_effect] to display text based on data from an external file, currently also included in the repository, fetching from outside is beyond the scope of my prototype.

    I _googled_ like crazy and read several fine StackOverflow and blog posts, where most of the responses where relying on jQuery solutions. Finally I came across [Mozilla Developer Network (MDN)][MDN].

    I created a JSON [data file](https://github.com/jonasbn/github-pages-javascript-prototype/blob/master/data.json
), mimicking the data from ["Terminal Text Effect"][terminal_text_effect].

    ```JSON
    {
        "words": ["Hello World, JavaScript is Awesome", "Console Text", "Made with Love."],
        "id": "text",
        "colors": ["tomato","rebeccapurple","lightblue"]
    }
    ```

    I implemented a XML HTTP request in [my JavaScript](https://github.com/jonasbn/github-pages-javascript-prototype/blob/master/experiment.js) to read the JSON file:

    ```javascript
    var oReq = new XMLHttpRequest();
    oReq.addEventListener("load", reqListener);
    oReq.open("GET", "data.json");
    oReq.send();
    ```

    And I implemented a listener:

    ```javascript
    function reqListener () {
        var obj = JSON.parse(this.responseText);
        consoleText(obj.words, obj.id, obj.colors);
    }
    ```

    So when the page has loaded [my JavaScript](https://github.com/jonasbn/github-pages-javascript-prototype/blob/master/experiment.js) reads the JSON data file and calls the awesome JavaScript from the _pen_ and I can now control the text rendered by changing and committing a new revision JSON data file.

    This all required alot of reading and experimentation (the number of commits shows), I needed to understand [XMLHttpRequest][mdn_xhr] and [JSON parsing][mdn_json_parse] and I really had a hard trying [get data out of the event listener][mdn_event_listener_data_out] until I understood the order of things.

    One thing I did learn from all of this is JavaScript programming and frontend development is not the same, it uses the same language, but the context of the browser is a very different world from doing katas or similar for learning JavaScript programming.

### Conclusion

The final solution is available [here](https://github.com/jonasbn/github-pages-javascript-prototype) and you can see it running [here](https://jonasbn.github.io/github-pages-javascript-prototype)

It took some time to get it to work, but I am glad that I could answer my original question and demonstrate the answer:

> Can you host semi-interactive pages with data using [GitHub Pages][github_pages]?

Programming is hard and wrapping your head around new concepts, technologies, challenges and constraints is hard, but it is also immensely fun and rewarding.

Reflecting on the process, I find that keeping the goal small and constrained and not letting the scope creep, lets you focus on the task at hand and the goal.

Yes the challenge might seem overly simple and it seems everybody else can solve it faster and better. Every time you run into a problem you are faced with imposter syndrome, but remember it is a process and you are learning.

I am expanding from having worked primarily with middle-tier and backend solutions for many years to the frontend. It is _very_ hard and I feel _stupid_ all the time. But in my experience when I have struggled long enough with a particular problem and have asked for help, people with more experience in the particular field have been incredibly helpful and have sent me in the right direction and have never experienced somebody pointing fingers.

So solving this basic task and getting helpful assistance when really needed, has really sparked my ambition to continue in this manner and there are plenty of next steps I can take from here.

## Next Step

[GitHub Pages][github_pages] is centered around [Jekyll](https://jekyllrb.com/), there are newer static site generator, which have evolved from where Jekyll originally _scratched an itch_.

I decided how to start with a _vanilla_ solution.

The next steps could be to delve into experiments/prototypes based on:

1. [Jekyll], getting more from the standard and by GitHub chosen static site generator
1. [Hugo], evaluating the use of an alternative static site generator
1. [Vue], not limiting implementation to vanilla JavaScript
1. [React], again not limiting implementation to vanilla JavaScript
1. [Svelte], and yet again not limiting implementation to vanilla JavaScript
1. [D3], perhaps even doing beautiful visualizations or graphs

These could all be basic proof of concept like projects. At some point I do however want to go deeper, based on a real project and of course the best fit candidate for the optimal solution.

The one thing that I would really like to try out at this time is extending the prototype with use of an external data source as stated previously I decided to host the data locally, so this step would be a natural path forward. This will push the work into the security realm and content security policies, so I expect I need to get a more thorough understanding of this especially in relation to [Github Pages][github_pages], but it would certainly bring more value to the table to be able to answer the extended question:

> Can you host semi-interactive pages with **external** data using [GitHub Pages][github_pages]?

## Resources

Thanks to all the people, who unknowningly have contributed to this work.

- [Tobias](https://codepen.io/Tbgse)
- [Tania Rascia](https://twitter.com/taniarascia)
- [Matt West](https://twitter.com/mattantwest)
- The people contributing to StackOverflow and Mozilla Developer Network

Almost all of the resources mentioned above are listed here:

- Example lifted from [Codepen.io]: ["Terminal Text Effect"][terminal_text_effect] by [Tobias](https://codepen.io/Tbgse)
- HTML skeleton from Blog post: ["Basic HTML5 Skeleton File"][basic_html5_skeleton_file] by [Tania Rascia](https://twitter.com/taniarascia)
- Experiment inspired by blog post: ["Using GitHub Pages To Host Your Website"][treehouse_blog] by [Matt West](https://twitter.com/mattantwest)

- [MDN: "Using XMLHttpRequest"][mdn_xhr]
- [MDN: `JSON.parse()`][mdn_json_parse]
- [MDN: "Getting Data Into and Out of an Event Listener Using Objects"](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener)
- [MDN: "Event reference"](https://developer.mozilla.org/en-US/docs/Web/Events)

[Codepen.io]: https://codepen.io/
[Hugo]: https://gohugo.io/
[Jekyll]: https://jekyllrb.com/
[Vue]: https://vuejs.org/
[React]: https://reactjs.org/
[Svelte]: https://svelte.dev/
[github_pages]: https://pages.github.com/
[Sass]: https://sass-lang.com/
[last_mover]: https://lastmover.wordpress.com/2017/01/01/github-pages/
[D3]: https://d3js.org/
[terminal_text_effect]: https://codepen.io/Tbgse/pen/dYaJyJ?editors=1000#0
[basic_html5_skeleton_file]: https://www.taniarascia.com/basic-html5-file/
[github-pages-javascript-prototype]: https://github.com/jonasbn/github-pages-javascript-prototype
[MDN]: https://developer.mozilla.org/en-US/
[treehouse_blog]: https://blog.teamtreehouse.com/using-github-pages-to-host-your-website
[mdn_xhr]: https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest/Using_XMLHttpRequest
[mdn_json_parse]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse
[mdn_event_listener_data_out]: https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener
