{% highlight javascript %}
{% include alert_msg.js %}
{% endhighlight %}

# [klasa 2](/klasa2.md)
# [klasa 3](/klasa3.md)


<script type="text/javascript" charset="utf-8">
    $(document).ready(function(){
      $("#submit").click(function(e){
        {% include alert_msg.js %}
        return false;
      })
    });
  </script>
