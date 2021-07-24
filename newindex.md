<meta content="IE=9" http-equiv="X-UA-Compatible"></meta><title>Perry's Web site</title><script src="js/jquery-1.6.2.min.js" type="text/javascript"></script><script src="js/referencetagging.js" type="text/javascript"></script><link href="css/page_style.css" rel="stylesheet" type="text/css"></link><style type="text/css">
div#menu_bar{
    top: 0px;
    left: 0px;
    margin-right: auto;
    padding: 0;
    position: fixed;
    text-align: left;
    overflow: visible;
/*    width: 100%;*/
}
div#under_menu{
    display: block;
    margin: 0px;
    padding: 0px;
}
div#menu_bar ul#menu_list{
    background-color: transparent;
    margin: 0px;
    padding: 0px;
}
div#menu_bar ul#menu_list li{
    background-color: #CCEEEE;
    margin: 0px 0px 0px 0px;
    box-shadow: 5px 5px 5px rgba(0,0,0,.5); /* w3c box shadow */
    -moz-box-shadow: 5px 5px 5px rgba(0,0,0,.5); /* mozilla box shadow */
    -webkit-box-shadow: 5px 5px 5px rgba(0,0,0,.5); /* webkit box shadow */
    padding: 3px 5px 3px 5px;
    display: inline-block;
    border-top: 2px solid #DDFFFF;
    border-left: 2px solid #DDFFFF;
    border-bottom: 2px solid #BBDDDD;
    border-right: 2px solid #BBDDDD;
    cursor: pointer;
}
div#menu_bar ul#menu_list li ul{
    border-top: 1px solid black;
    margin: 4px -5px -3px -5px;
    padding: 0;
    position: fixed;
    background-color: #CCEEEE;
/*    opacity: 0.9;*/
    text-align: left;
    list-style-type: none;
    box-shadow: 5px 5px 5px rgba(0,0,0,.5); /* w3c box shadow */
    -moz-box-shadow: 5px 5px 5px rgba(0,0,0,.5); /* mozilla box shadow */
    -webkit-box-shadow: 5px 5px 5px rgba(0,0,0,.5); /* webkit box shadow */
}
div#menu_bar ul#menu_list li ul li{
/*    opacity: 1;*/
    margin: 0px;
    display: list-item;
}
div#content{
    min-width: 460px;
}
.parent_item{
}
div#menu_bar ul#menu_list li:hover{
    text-decoration: underline;
    
}
div#menu_bar ul#menu_list li.parent_item:hover{
    text-decoration: none;
    background-color: #DDF0F0;
    border-top: 2px solid #EEFFFF;
    border-left: 2px solid #EEFFFF;
    border-bottom: 2px solid #CCE0E0;
    border-right: 2px solid #CCE0E0;
}

</style><script type="text/javascript">
var default_title = "Perry's Web site";
var default_page = './noframesindex.html';
var current_page;
var url_prefix = window.location.protocol+'//'+window.location.host+window.location.pathname;
var hash_flag = false;
var top_of_page;

function apply_reftagger()
{
    ref_tag_load();
    Logos.ReferenceTagging.lbsBibleVersion = "HCSB";
    Logos.ReferenceTagging.lbsLinksOpenNewWindow = true;
    Logos.ReferenceTagging.lbsAddLibronixDLSLink = true;
    Logos.ReferenceTagging.lbsLogosBibleVersion = "HCSB";
    Logos.ReferenceTagging.lbsLogosLinkIcon = "dark";
    Logos.ReferenceTagging.lbsNoSearchTagNames = [ "h2", "h3", "h3" ];
    Logos.ReferenceTagging.lbsTargetSite = "biblia";
    //Logos.ReferenceTagging.lbsConvertHyperlinks = true;
    Logos.ReferenceTagging.tag();
    /*$.getScript("http://bible.logos.com/jsapi/referencetagging.js",function(){
        Logos.ReferenceTagging.lbsBibleVersion = "HCSB";
        Logos.ReferenceTagging.lbsLinksOpenNewWindow = true;
        Logos.ReferenceTagging.lbsAddLibronixDLSLink = true;
        Logos.ReferenceTagging.lbsLogosBibleVersion = "HCSB";
        Logos.ReferenceTagging.lbsLogosLinkIcon = "dark";
        Logos.ReferenceTagging.lbsNoSearchTagNames = [ "h2", "h3", "h3" ];
        Logos.ReferenceTagging.lbsTargetSite = "biblia";
        Logos.ReferenceTagging.tag();
    });*/
}

function getUrlVars()
{
    var vars = [], hash;
    var href = window.location.href;
    var start = href.lastIndexOf('?') + 1, end = href.lastIndexOf('#');
    if(end<=start)
        end = href.length;
    else
        vars['#']=href.slice(end+1);
    var hashes = href.slice(start,end).split('&');
    for(var i = 0; i < hashes.length; i++)
    {
        hash = hashes[i].split('=');
        vars.push(hash[0]);
        vars[hash[0]] = hash[1];
    }
    return vars;
}

function menu_item(name,url,children){
    this.name=name;
    this.url=url;
    this.children=children;
    this.build_menu=function(){
        var temp = '<li url="'+this.url+'">'+this.name;
        if(children && children.length>0){
            temp+='<ul>';
            for(var x=0; x<children.length; x++)
                temp+=children[x].build_menu();
            temp+='';
        }
        return temp+'';
    }
}

var menu_array = new Array(new menu_item('Home','',new Array()),
    new menu_item('Confessions of Faith','./confess.html',new Array(
        new menu_item('Confessions of Faith','./confess.html',new Array()),
        new menu_item('What Southern Baptists Believe','http://www.sbc.net/aboutus/basicbeliefs.asp',new Array()),
        new menu_item('Baptist Faith and Message (SBC 2000)','http://www.sbc.net/bfm/bfm2000.asp',new Array()),
        new menu_item('The Mysteries of Christianity','mysteries.html',new Array()),
        new menu_item('Personal Testimonies','./testimon.html',new Array()),
        new menu_item('Scriptural Impacts','./impacts.html',new Array()),
        new menu_item('The Original Languages of the Bible','./languages.html',new Array()),
        new menu_item('My Prayer','./prayer.html',new Array()))),
    new menu_item('Where I Stand','./stance.html',new Array(
        new menu_item('Where I Stand','./stance.html',new Array()),
        new menu_item('Abortion','./abortion2.html',new Array()),
        new menu_item('The First Amendment','./1stamendment.html',new Array()),
        new menu_item('Religious Freedom','./freedom.html',new Array()),
        new menu_item('Why Has Violence Increased in Public Schools?','./violence.html',new Array()),
        new menu_item('Marriage, Divorce, and Human Sexuality','./marriage.html',new Array()),
        new menu_item('Homosexuality','./homosexual2.html',new Array()),
        new menu_item('A Modern Rendering of A Christmas Carol','./christmascarol.html',new Array()),
        new menu_item('What Defines a Real Hero?','./heroes.html',new Array()))),
    new menu_item('Scriptural Impacts','./impacts.html',new Array(
        new menu_item('Outline','./impacts.html#top',new Array()),
        new menu_item('Introduction','./impacts.html#into',new Array()),
        new menu_item('Making Decisions','./impacts.html#way',new Array()),
        new menu_item('Knowing the Truth','./impacts.html#truth',new Array()),
        new menu_item('Abundant Living','./impacts.html#life',new Array()),
        new menu_item('The Last Times','./impacts.html#last',new Array()))),
    new menu_item('Philosophical Questions','./philosop.html',new Array()),
    new menu_item('Receive a New Life','./gospel.html',new Array()),
    new menu_item('Links','./links.html',new Array()));

function load_url(url){
    if(url=='')
        url=default_page;
    $.ajax({url: url,
        success: function(data) {
            $('body div#content').children().remove();
            $('body div#content').html(data);
            var title = $('body div#content').find('title').remove();
            if(title.length>0) document.title=$(title).html();
            else document.title=default_title;
            $('body div#content').find('a').each(function() {
                var link=this.getAttribute('href', 2);
                if(link){
                    if(link.search(/[a-zA-z]+\:/)==-1) {
                        $(this).attr('url',link);
                        if(link[0]=='#') {
                            $(this).addClass('local_target');
                            link=url+link;
                        } else
                            $(this).addClass('local_link');
                        $(this).prop('href',url_prefix+'?subpage='+link);
                    } else {
                        $(this).prop('target','_blank');
                        if(link.search(/http\:\/\/www\.biblegateway/)!=-1 && ! $(this).hasClass('exception')) //remove old links
                            $(this).replaceWith($(this).html());
                        if(link.search(/libronixdls\:/)!=-1) //remove old links
                            $(this).remove();
                    }
                }
            });
            apply_reftagger();
            var target = getUrlVars()['#'];
            if(target){
                var elem = $('[name="'+target+'"]')
                if(elem.length>0) elem[0].scrollIntoView(true);
                else top_of_page.scrollIntoView(true);
            }
            else top_of_page.scrollIntoView(true);
        },
        error: function(jqXHR, textStatus, errorThrown){
            $('body div#content').children().remove();
            $('body div#content').html('<div class="page_style"><h2>Error: '+errorThrown+'');
        }
    });
}

$(document).ready(function(){
    //function to resize the div under the menu to match the menu so that the content displays at the correct height
    $(window).resize(function(){var temp=$('div#menu_bar').outerHeight(); $('div#under_menu').html('Test: '+temp).height(temp);});
    var temp = "<ul id='menu_list'>";
    for(var x=0; x<menu_array.length; x++)
        temp+=menu_array[x].build_menu();
    $('body div#menu_bar').html(temp+='');

    //hide all the submenus
    $('div#menu_bar ul#menu_list').find('ul').hide();
    //code to show and hide menus by clicking
    $('div#menu_bar ul#menu_list').find('ul').parent('li').addClass('parent_item');
    $('.parent_item').click(function(event){
        if(this==event.currentTarget){
            $('div#menu_bar ul#menu_list').find('ul').not(':hidden').not($(this).parents('ul')).not($(this).children('ul')).hide();
            $(this).children('ul').slideToggle('fast');
        }
        return false;
    });
    
    //deactive certain a-tag links
    $(".prevent_default").live('click',function(event){ event.preventDefault(); });
    
    //behavor of relative links
    $(".local_link").live('click',function(event){ event.preventDefault(); window.location.hash='?subpage='+$(this).attr('url'); return false;});

    //behavor of targets links
    $(".local_target").live('click',function(event){
        event.preventDefault();
        hash_flag=true;
        window.location.hash='?subpage='+getUrlVars()['subpage']+$(this).attr('url');
        return false;
    });

    //code to follow urls
    $('div#menu_bar ul#menu_list').find('li').not('.parent_item').click(function(){
        $('div#menu_bar ul#menu_list').find('ul').not(':hidden').slideUp('fast');
        var target=$(this).attr('url');
        if(target.search(/[a-zA-z]+\:/)!=-1)
            window.open(target);
        else
            window.location.hash='?subpage='+target;
        return false;
    }).each(function(){
        $(this).wrapInner('<a class="prevent_default" href="?subpage='+$(this).attr('url')+'">');
    });

    //set the inital height of the underlying div
    $('div#under_menu').height($('div#menu_bar').outerHeight());

    $(window).bind('hashchange',function(event){
        var hash = window.location.hash;
        if(!hash || hash=='')
            hash='?subpage='+default_page;
        var url_vars = getUrlVars();
        var location = url_vars['subpage'];
        if(location=='newindex.html')
            location=default_page;
        if(hash_flag) {
            var target = url_vars['#'];
            if(target) $('[name="'+target+'"]')[0].scrollIntoView(true);
            hash_flag=false;
        } else if(hash[1]=='?'||hash[0]=='?') {
            load_url(location?location:default_page);
        }
        return true;
    });

    top_of_page = $('#under_menu')[0];

    //load the default page
    var url_vars = getUrlVars();
    var location = url_vars['subpage'];
    if(location=='newindex.html')
        location=default_page;
    load_url(location?location:default_page);
});
</script></head><body><div id="under_menu"></div><div id="menu_bar"></div><div id="content">loading ...</div>