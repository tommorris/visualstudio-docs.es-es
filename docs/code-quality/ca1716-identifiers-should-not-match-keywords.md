---
title: 'CA1716: Los identificadores no deberían coincidir con palabras clave'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
helpviewer_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b5ee844da2c04a1dd6eac6a7ca458957dd22a71
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45550614"
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716: Los identificadores no deberían coincidir con palabras clave
|||
|-|-|
|TypeName|IdentifiersShouldNotMatchKeywords|
|Identificador de comprobación|CA1716|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un nombre de un espacio de nombres, un tipo o miembro virtual o de interfaz coincide con una palabra clave reservada en un lenguaje de programación.

## <a name="rule-description"></a>Descripción de la regla
 Los identificadores para los espacios de nombres, tipos y virtual y los miembros de interfaz no deberían coincidir con palabras clave definidas por los lenguajes que tienen como destino common language runtime. Según el idioma que se usa y la palabra clave, las ambigüedades y errores del compilador pueden dificultar la biblioteca usar.

 Esta regla comprueba las palabras clave en los idiomas siguientes:

- Visual Basic

- C#

- C++/CLI

 Comparación entre mayúsculas y minúsculas se utiliza para [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] comparación distingue mayúsculas de minúsculas y palabras clave se usa para los demás idiomas.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Seleccione un nombre que no aparece en la lista de palabras clave.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Puede suprimir una advertencia de esta regla si están convencidos de que el identificador no confundirá a los usuarios de la API, y que la biblioteca se puede usar en todos los idiomas disponibles en el [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].