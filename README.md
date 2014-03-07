# Why I JavaScript (in 300 seconds)
## Informatics and Bio-Computing Retreat, March 4th, 2014

This lightning talk was mostly using the console to write and run javascript on
the fly. I ignored some best practices to minimize typing - read a detailed
explanation in an upcoming blog post.


First, open Chrome with the disable-web-security flag. The ICGC data portal api
(dcc.icgc.org/api) doesn't currently allow cross-origin resource sharing. (Or
  you can pick a different api)

    // Make sure you completely close Chrome first
    open -a Google\ Chrome --args --disable-web-security

In the browser, right-click on the '300' text. Select
'Inspect Element'.

In the console:

    // Turn '300' into a countdown
    var text = $0
    setInterval(function(){
        text.textContent = parseInt(text.textContent)-1
    },1000)

    // Change countdown colour
    text.style.color = 'blue'

    // Set then reset countdown value
    text.textContent = 1000
    text.textContent = 240

    // Load in a WormBase widget
    $('#content').load('http://www.wormbase.org/rest/widget/gene/WBGene00006760/overview')

    // Fetch search data from the ICGC data portal
    $.get('http://dcc.icgc.org/api/search?q=P53', function(d){data=d})

    // Pretty print the JSON in the DOM, then remove
    $('pre').html(JSON.stringify(data.hits, null, ' '))
    $('pre').empty()

    // Create a bar chart graphing the score of each search result
    var chart = new JSChart('content', 'bar')
    chart.setDataArray(data.hits.map(function(item){
        return [item.id, item.score]
    }))
    chart.draw()
