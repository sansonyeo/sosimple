---
title: "웹서비스 호출 테스트"
excerpt: "> 웹서비스 호출 테스트"
categories:
- Story
tags:
  - IT
  - WebService
---


<script type="text/javascript" src="http://ajax.googleapis.com/ajax/libs/jquery/1.8.3/jquery.min.js"></script>
<script type="text/javascript">
    $(document).ready(function () {
        $("[id*=btnExec]").click(function () {
            var txtTableName = $("[id*=txtTableName]").val();
            var txtCondition = $("[id*=txtCondition]").val();

            $.ajax({
                type: "POST",
                url: "http://121.167.154.99:86/WebService1.asmx/SelectTable",
                data: "{ table_Name: '" + txtTableName + "', condition: '" + txtCondition + "'}",
                contentType: "application/json; charset=utf-8",
                dataType: "json",
                success: function (r) {
                    alert(r.d);
                },
                error: function (r) {
                    alert(r.responseText);
                },
                failure: function (r) {
                    alert(r.responseText);
                }
            });
            return false;
        });
    });
</script>