---
title: "Shortcode"
date: 2020-06-08T08:06:25+06:00
description: Shortcodes sample
menu:
  sidebar:
    name: shortcode
    identifier: shortcodes
    weight: 40

draft: True
---



## test

test
{{< alert type="success" >}}
 `type="success"` 
{{< /alert >}}

{{< alert type="danger" >}}
test `type="danger"` test
{{< /alert >}}

{{< alert type="warning" >}}
t `type="warning"` 
{{< /alert >}}

{{< alert type="info" >}}
tes `type="info"` 
{{< /alert >}}

{{< alert type="dark" >}}
t `type="dark"` t
{{< /alert >}}

{{< alert type="primary" >}}
t `type="primary"` t
{{< /alert >}}

{{< alert type="secondary" >}}
t `type="secondary"` t
{{< /alert >}}

## yes

#### tset

{{< img src="/posts/shortcodes/boat.jpg" title="A boat at the sea" >}}

{{< vs 3 >}}

#### `height` and `width` attribute yes

{{< img src="/posts/shortcodes/boat.jpg" height="400" width="600" title="A boat at the sea" >}}

{{< vs 3 >}}

#### `height` এবং `width` attribute blabla

{{< img src="/posts/shortcodes/boat.jpg" height="400" width="600" align="center" title="A boat at the sea" >}}

{{< vs 3 >}}

#### `float` attribute test

{{< img src="/posts/shortcodes/boat.jpg" height="200" width="500" float="right" title="A boat at the sea" >}}

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Cras egestas lectus sed leo ultricies ultricies. Praesent tellus risus, eleifend vel efficitur ac, venenatis sit amet sem. Ut ut egestas erat. Fusce ut leo turpis. Morbi consectetur sed lacus vitae vehicula. Cras gravida turpis id eleifend volutpat. Suspendisse nec ipsum eu erat finibus dictum. Morbi volutpat nulla purus, vel maximus ex molestie id. Nullam posuere est urna, at fringilla eros venenatis quis.

Fusce vulputate dolor augue, ut porta sapien fringilla nec. Vivamus commodo erat felis, a sodales lectus finibus nec. In a pulvinar orci. Maecenas suscipit eget lorem non pretium. Nulla aliquam a augue nec blandit. Curabitur ac urna iaculis, ornare ligula nec, placerat nulla. Maecenas aliquam nisi vitae tempus vulputate.

## test

testtt
#### testtttt

{{< split 6 6>}}

##### testttttt

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Cras egestas lectus sed leo ultricies ultricies.

---

##### yes

Fusce ut leo turpis. Morbi consectetur sed lacus vitae vehicula. Cras gravida turpis id eleifend volutpat.

{{< /split >}}

#### no

{{< split 4 4 4 >}}

##### yes

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Cras egestas lectus sed leo ultricies ultricies.

---

##### no
Aenean dignissim dictum ex. Donec a nunc vel nibh placerat interdum. 

---

##### test

Fusce ut leo turpis. Morbi consectetur sed lacus vitae vehicula. Cras gravida turpis id eleifend volutpat.

{{< /split >}}

## final test

test
test{{< vs 4>}}
test `4rem` test