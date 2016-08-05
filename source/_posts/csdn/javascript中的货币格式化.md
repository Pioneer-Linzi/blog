---
title: javascript 中的货币格式化
date: 2015-05-04 10:51:11
tags: javascript
---

```
<script>
    function cc(s){
        if(/[^0-9\.]/.test(s)) return "invalid value";
        s=s.replace(/^(\d*)$/,"$1.");
        s=(s+"00").replace(/(\d*\.\d\d)\d*/,"$1");
        s=s.replace(".",",");
        var re=/(\d)(\d{3},)/;
        while(re.test(s))
            s=s.replace(re,"$1,$2");
        s=s.replace(/,(\d\d)$/,".$1");
        return "￥" + s.replace(/^\./,"0.")
    }
</script>
<input onchange="this.value=cc(this.value)">
```

