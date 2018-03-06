$(document).ready(function () {
    GetNavigatorData();
    GetbannerData();
});

function GetNavigatorData() {
    $('#ImgLoadingNavigator').show();
    $.ajax({
        type: "POST",
        url: apiUrl + '/CareerNavigator/GetCurrentNavigatorData',
        contentType: "application/json",
        dataType: "json",
        async: true,
        cache: false,
        success: function (msg) {
            $('#ImgLoadingNavigator').hide();
            if (msg.GraphText != null) {
                $("#divMain").show();
                $("#divchartdata").html(msg.GraphText);
                $("#divzaxis").html(msg.ZaxisText);
                $("#divxaxis").html(msg.XaxisText);
                $("#divyaxis").html(msg.YaxisText);
            }
            else {
                $("#divMain").hide();
            }
        },
        error: function (x, e) {
            window.location = apiUrl + "/Home/Error";
        }
    })
}
