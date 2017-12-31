
# Toothrot IDE Download

<button class="ide-download-button">
    Download Toothrot IDE
</button>

<script>
(function () {
    
    var button = document.querySelector(".ide-download-button");
    var os = "Unknown OS";
    var appVersion = navigator.appVersion;
    
    if (appVersion.indexOf("Win") != -1) {
        os = "Windows";
    }
    
    if (appVersion.indexOf("Mac") != -1) {
        os = "Mac OS X";
    }
    
    if (appVersion.indexOf("X11") != -1) {
        os = "UNIX";
    }
    
    if (appVersion.indexOf("Linux") != -1) {
        os = "Linux";
    }
    
    button.innerHTML += " for " + os;
    
    button.addEventListener("click", function () {
        console.log("Download button clicked");
    });
    
}());
</script>
