---
title: 计算函数社区列表
layout: default
parent: 计算函数
---

# 计算函数(第三方)
{: .d-inline-block }

函数
{: .label .label-green }

由社区提供计算函数配置

<div id=table class='table-wrapper'></div>

<script>
var http = new XMLHttpRequest();
http.open('get', '/config/calcFunction/recommendeds.json', true);
http.send();
http.onreadystatechange = function () {
    if (http.readyState == 4 && http.status == 200) {
        var jsonData = JSON.parse(http.response);
        var table = document.createElement('table');
        var thead = document.createElement('thead');
        var tbody = document.createElement('tbody');
    
        var keys = jsonData.child;
        var headerRow = document.createElement('tr');
    
        ['Name', 'Path'].forEach(function(i) {
            var th = document.createElement('th');
            th.textContent = i;
            headerRow.appendChild(th);
        });
    
        thead.appendChild(headerRow);
        table.appendChild(thead);
    
        jsonData.child.forEach(function(item) {
            var row = document.createElement('tr');
            var tdName = document.createElement('td'),
                tdPath = document.createElement('td');

                tdName.textContent = item["name"];
                tdPath.innerHTML = item["updataFunction"].map((pathItem) => `<div><b>${pathItem.name}</b>:</div><a href='${pathItem.path}'>${pathItem.path}</a>`);

            row.appendChild(tdName);    
            row.appendChild(tdPath);
            tbody.appendChild(row);
        });
    
        table.appendChild(tbody);

        document.getElementById('table').appendChild(table);
    }
}


</script>

# 提供你的函数

前往**[此处](https://github.com/hell-gun-calculator/document/)**克隆项目,修改后提交新合并请求，确认正式无误，管理将合并主仓库。

需要注意几点:

- 在**[calcFunction/recommendeds.json](https://github.com/hell-gun-calculator/document/blob/main/config/calcFunction/recommendeds.json)**列表里添加你的来源信息 
- 在**[目录](https://github.com/hell-gun-calculator/document/blob/main/config/calcFunction/)**创建你的.json配置文件，具体信息参考**[演示文件](https://github.com/hell-gun-calculator/document/blob/main/config/calcFunction/example.json)**