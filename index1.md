 <meta content="IE=9" http-equiv="X-UA-Compatible"></meta><title>Image test</title><style type="text/css">
h1 {
color: #d12;
-webkit-mask-image: -webkit-gradient(linear, left top, left bottom, from(rgba(0,0,0,1)), to(rgba(0,0,0,0)));
text-shadow: -3px 0 4px 0 #006;
  }
</style></head><body>Heading
=======

![image](jan2011_005.jpg)<div id="main"></div><script src="jquery-1.4.4.js" type="text/javascript"></script></body></html><html><script type="text/javascript">
    images = document.getElementsByTagName("img");
    for(i in images)
    {
        i.onclick = function(){ alert(""+i.src); };
        $(main).css("border","9px solid red");
    }
    $(document).ready(function() {
        $("img").css("border","9px solid blue");

        $("img").click(function(eventObject) {
            temp = $(this).attr("src");
            alert(" "+temp);
            $(this).css("border","9px solid green");
        });
    });
</script></html>