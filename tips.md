# iframe loading timeout

    function setIframeSrc() {
    var s = "http://lx5.in/CGIT-Results-p2-2013.php";
    var iframe1 = document.getElementById('iframe1');
    iframe1.src = s;
    setTimeout(function(){
        if (window.stop) {
            window.stop();
        } else {
            document.execCommand('Stop'); // MSIE
        }
    }, 5000);
    }
    setTimeout(setIframeSrc, 5000);
