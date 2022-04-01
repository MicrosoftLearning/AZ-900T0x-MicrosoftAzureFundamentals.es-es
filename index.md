---
title: Instrucciones hospedadas en línea
permalink: index.html
layout: home
ms.openlocfilehash: c8816b7d9de9c19fbd4c6b3f373d6e4336c6ca5a
ms.sourcegitcommit: 26c283fffdd08057fdce65fa29de218fff21c7d0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/27/2022
ms.locfileid: "137908668"
---
# <a name="content-directory"></a>Directorio de contenido

Hipervínculos a cada uno de los tutoriales. Los instructores pueden optar por usar el tutorial como una demostración o un laboratorio de alumnos. 

## <a name="walkthroughs"></a>Tutoriales

{% assign wts = site.pages | where_exp:"page", "page.url contains '/Instructions/Walkthroughs'" %}
| Módulo | Tutorial |
| --- | --- | 
{% for activity in wts %}| {{ activity.wts.module }} | [{{ activity.wts.title }}{% if activity.wts.type %} - {{ activity.wts.type }}{% endif %}]({{ site.github.url }}{{ activity.url }}) |
{% endfor %}

