<！DOCTYPE html >
< html >

<头>
    < meta  charset =“ utf-8 ” >

    < title >合成大西瓜</ title >

    <！--http：//www.html5rocks.com/en/mobile/mobifying/-->
    < meta  name =“ viewport ” content =“ width = device-width，user-scalable = no，initial-scale = 1，minimum-scale = 1，maximum-scale = 1 ” />

    <！--https：//developer.apple.com/library/safari/documentation/AppleApplications/Reference/SafariHTMLRef/Articles/MetaTags.html-->
    < meta  name =“ apple-mobile-web-app-capable ” content =“ yes ” >
    < meta  name =“ apple-mobile-web-app-status-bar-style ” content =“ black-translucent ” >
    < meta  name =“ format-detection ” content =“ phone = no ” >

    <！-在360上强制使用webkit->
    < meta  name =“ renderer ” content =“ webkit ” />
    <元 名称=“强制渲染” content =“ webkit ” />
    <！-IE上的强制边缘->
    < meta  http-equiv =“ X-UA-Compatible ” content =“ IE = edge，chrome = 1 ” />
    < meta  name =“ msapplication-tap-highlight ” content =“ no ” >

    <！-在某些浏览器上强制全屏->
    < meta  name =“全屏” content =“ yes ” />
    < meta  name =“ x5-fullscreen ” content =“ true ” />
    < meta  name =“ 360-fullscreen ” content =“ true ” />

    <！-在某些浏览器上强制屏幕方向->
    <元 名称=“屏幕方向” content =“” />
    < meta  name =“ x5-orientation ” content =“” >

    <！-修复fireball / issues / 3568->
    <！-<元名称=“浏览器模式” content =“应用”>->
    < meta  name =“ x5-page-mode ” content =“ app ” >

    <！-<link rel =“ apple-touch-icon” href =“。png” />->
    <！-<link rel =“ apple-touch-icon-precomposed” href =“。png” />->


    <！-<脚本>
        pushHistory（）;
        window.addEventListener（“ popstate”，function（e）{
        }，错误）；
        函数pushHistory（）{
            var state = {
                标题：“”，
                网址：window.location.href
            };
            window.history.pushState（state，state.title，state.url）;
        }
    </ script>->
    <！-<script type =“ text / javascript”>
        var agent = navigator.userAgent.toLowerCase（）;
        if（agent.indexOf（“ qbwebviewtype”）> 0）{
           location.href =“ http://g.fromgame.com/game/462/”;
        }
    </ script>->

    < link  rel =“ stylesheet ” type =“ text / css ” href =“ style-mobile.css ” />

</头>

<正文 样式=“ margin：0;背景：#ddd; ” align =“ center ” >
    < div 样式=“ align：center; display：none ” > < img  src =“ res / share.jpg ” width =“ 10％ ” /> </ div >

    < div  id =“ canvasDiv ” style =“ width：100％; height：100％; ” >
        < canvas  id =“ GameCanvas ” oncontextmenu =“ event.preventDefault（） ” tabindex =“ 0 ” > </ canvas >
        < div  id =“ block-Box ”样式=“ display：block; width：100％; height：100％; ” > </ div >
    </ div >



    < div  id =“ adContainer ”样式=“ display：none; position：absolute; top：0px; left：0px; width：100％; height：100％; z-index：999; ” > </ div >
    < div  id =“ loadingText ” style =“宽度：100％;显示：无; text-align：center; position：absolute; top：45％; z-index：2; font-size：20px; color：＃f99f0a “ >
        加载中...... 0％
    </ div >

    < div  id =“ splash ” >
        <！-<div class =“ progress-bar bars”>->
        <！-<span style =“ width：0％”> </ span>->
        <！-</ div>->
    </ div >

    < div  id =“ loadingImg ” style =“ top：45％; width：100％; position：absolute; ” >
        < img  src =“ res / loading.gif ”宽度=“ 20％ ”高度=“ 20％ ” />
    </ div >




    <！-<div align =“ center” style =“字体大小：10像素；颜色：dimgrey”>广告</ div>->


    <脚本 src =“ src / settings.js ” charset =“ utf-8 ” > </脚本>

    <脚本 类型=“ text / javascript ” >
        var  preloader ;
        var  adCompleteFlag  =  false ;
        var  resCompleteFlag  =  false ;

        var  adEndComplete  =  false ;
        var  resEndComplete  =  false ;

        JusticeLanTitle （）;

        函数 JusticeLanTitle （） {
            // console.log（“ window.navigator.language”，window.navigator.language）;

            如果 （窗口。导航。语言 ==  “ZH-CN”  || 窗口。导航。语言 ==  “ZH-CN” ） {
                文件。title  =  “合成大魔恋” ;
            } 


        }

        var  loadintT  =  document 。getElementById （“ loadingText” ）;
        var  loadintGif  =  document 。getElementById （“ loadingImg” ）
        setTimeout （function （） {
            loadintGif 。删除（）;
            loadintT 。风格。显示 =  “”
            updateLabView （0.1 ）;
        } ， 1 * 1000 ）

        窗口。计时器 =  null ;
        窗口。tempSeconds  =  1 ;
        窗口。loadData  =  { } ;
        loadData 。completeCount  =  0 ;
        loadData 。totalCount  =  0 ;

        onload （）;

        函数 onload （） {
            var  winHeight  =  document 。documentElement 。clientHeight ;
            文件。getElementById （“ canvasDiv” ）。风格。height  =  winHeight  +  “ px” ;
        } ;
        窗口。onload  = 函数（） {
            文件。getElementById （“ block-Box” ）。风格。显示 =  “无” ；
        }

        函数 updateLabView （t ） {
            if  （timer！= null ） {
                clearInterval （计时器）;
            }
            计时器 =  setInterval （函数（） {
                tempSeconds ++ ;
                actualTotal （）;
                var  loadintT  =  document 。getElementById （“ loadingText” ）
                如果 （！loadintT ） {
                    回报;
                }
                loadintT 。innerHTML  =  '正在加载...'  +  parseInt （tempSeconds ） +  '％' ;

                开关 （tempSeconds ） {
                    案例 20：
                        updateLabView （0.2 ）;
                        休息;
                    案例 40：
                        updateLabView （0.3 ）;
                        休息;
                    案例 60：
                        updateLabView （0.4 ）;
                        休息;
                    案例 96：
                        updateLabView （5 ）;
                        休息;
                    案例 97：
                        updateLabView （10 ）;
                        休息;
                    案例 98：
                        updateLabView （50 ）;
                        休息;
                    案例 99：
                        updateLabView （100 ）;
                        休息;
                    默认值：
                        如果 （tempSeconds > = 80  &&  tempSeconds  <  96 ） {
                            updateLabView （t  +  0.1 ）;
                        }
                        休息;
                }
                如果 （tempSeconds  >  100 ） {
                    clearInterval （计时器）;
                    tempSeconds  =  100
                    loadintT 。innerHTML  =  '正在加载...'  +  parseInt （tempSeconds ） +  '％' ;
                }
            } ， t * 1000 ）;
        }

        函数 actualTotal （） {
            VAR 百分比 =  parseInt函数（100 * loadData 。completedCount / loadData 。TOTALCOUNT ）;
            如果 （百分比 >  tempSeconds  &&  loadData 。TOTALCOUNT  >  1 ） {
                tempSeconds  = 百分比；
            }
        }


        / * setTimeout（“ ShowBannerAD（）”，“ 2000”）; * /
    </脚本>





    <脚本 src =“ src / settings.js ” charset =“ utf-8 ” > </脚本>

    <脚本 src =“ main.js ” charset =“ utf-8 ” > </脚本>


    <脚本 类型=“ text / javascript ” >
        （函数（） {
            //打开Web调试器控制台
            如果 （typeof  VConsole！== 'undefined' ） {
                窗口。vConsole  = 新的 VConsole （）;
            }

            var  splash  =  document 。getElementById （'splash' ）;
            飞溅。风格。显示 =  '块' ;


            控制台。日志（“ indexlTextTTTT” ）;

            var  cocos2d  =  document 。createElement （'script' ）;
            cocos2d 。异步 =  true ;
            cocos2d 。src  =  window 。_CCSettings 。调试？'cocos2d-js.js'：'cocos2d-js-min.js' ;

            var  engineLoaded  =  function （） {
                文件。身体。removeChild （cocos2d ）;
                cocos2d 。removeEventListener （'load' ， engineLoaded ， false ）;
                窗口。boot （）;
            } ;
            cocos2d 。addEventListener （'load' ， engineLoaded ， false ）;
            文件。身体。appendChild （cocos2d ）;
        } ）（）;
    </脚本>




</ body >

</ html >
