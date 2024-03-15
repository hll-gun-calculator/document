---
title: 版本
layout: default
nav_order: 2
---

# 版本
## 当前版本
<div id=newVersion></div>

<script>
var httpNewVersion = new XMLHttpRequest();
httpNewVersion.open('get', '/config/newVersion.json', true);
httpNewVersion.send();
httpNewVersion.onreadystatechange = function () {
    if (httpNewVersion.readyState == 4 && httpNewVersion.status == 200) {
        let jsonData = JSON.parse(httpNewVersion.response);
        let _versions = document.createElement('div'),_versionHtmlTable = "",_versionHtmlRow = "";
        Object.entries(jsonData).forEach((i) => {
            _versionHtmlRow += `<tr><td>${i[0] || 'N/A'}</td><td>${i[1].version || 'N/A'}</td><td>${i[1].buildNumber || 'N/A'}</td></tr>`;
        });

        _versionHtmlTable += `
<table>
    <thead>
        <tr><th>平台</th><th>版本</th><th>构建版本</th></tr>
    </thead>
    <tbody>${_versionHtmlRow}</tbody>
</table>
`;
        _versions.innerHTML = _versionHtmlTable;

        document.getElementById('newVersion').appendChild(_versions);
    }
}


</script>


----

## 历史版本

<div id=versions></div>

<script>
var httpVersions = new XMLHttpRequest();
httpVersions.open('get', '/config/versions.json', true);
httpVersions.send();
httpVersions.onreadystatechange = function () {
    if (httpVersions.readyState == 4 && httpVersions.status == 200) {
        let jsonData = JSON.parse(httpVersions.response);
        let _versions = document.createElement('div'),_versionHtmlTable = "",_versionHtmlRow = "", _versionHtmlContent = "";
        jsonData.list.forEach((i) => {
            Object.entries(i.system).forEach((systemItem) => {
                _versionHtmlRow += `<tr><td>${systemItem[0] || 'N/A'}</td><td>${systemItem[1].version || 'N/A'}</td><td>${systemItem[1].buildNumber || 'N/A'}</td></tr>`;
            });
            _versionHtmlContent = i.content ?? '';
            _versionHtmlTable += `
<h2>${i["version"]}</h2>
<table>
    <thead>
        <tr><th>平台</th><th>版本</th><th>构建版本</th></tr>
    </thead>
    <tbody>${_versionHtmlRow}</tbody>
</table>
`;
        });
        _versions.innerHTML = _versionHtmlTable + _versionHtmlContent;

        document.getElementById('versions').appendChild(_versions);
    }
}


</script>
