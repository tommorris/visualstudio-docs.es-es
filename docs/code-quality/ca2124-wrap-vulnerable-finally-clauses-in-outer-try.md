---
title: 'CA2124: Incluir cláusulas Finally vulnerables en un bloque Try externo'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
helpviewer_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
ms.assetid: 82efd224-9e60-4b88-a0f5-dfabcc49a254
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 738c214e845cb962bc6c28aa63806dee2858c295
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551245"
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124: Incluir cláusulas Finally vulnerables en un bloque Try externo

|||
|-|-|
|TypeName|WrapVulnerableFinallyClausesInOuterTry|
|Identificador de comprobación|CA2124|
|Categoría|Microsoft.Security|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 En las versiones 1.0 y 1.1 de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], un método público o protegido contiene un `try` / `catch` / `finally` bloque. El `finally` bloque aparece para restablecer el estado de seguridad y no se incluye en un `finally` bloque.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla busca `try` / `finally` bloques de código que tenga como destino las versiones 1.0 y 1.1 de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que podrían ser vulnerables a los filtros de excepción malintencionados presentes en la pila de llamadas. Si se producen operaciones confidenciales como la suplantación en el bloque try, y se produce una excepción, el filtro puede ejecutarse antes de la `finally` bloque. El ejemplo de suplantación, esto significa que el filtro se ejecutaría como el usuario suplantado. Los filtros son actualmente sólo pueden implementarse en Visual Basic.

> [!NOTE]
> En las versiones 2.0 y versiones posteriores de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], protege automáticamente el tiempo de ejecución un `try` / `catch` /  `finally` block de los filtros de excepción malintencionados, si se produce el restablecimiento directamente dentro del método que contiene el bloque de excepción.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Coloque el desencapsulado `try` / `finally` en un bloque try externo. Vea el segundo ejemplo siguiente. Esto obliga la `finally` se ejecute antes de código de filtro.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="pseudo-code-example"></a>Ejemplo de pseudocódigo

### <a name="description"></a>Descripción

El pseudocódigo siguiente muestra el patrón que detecta esta regla.

```csharp
try {
   // Do some work.
   Impersonator imp = new Impersonator("John Doe");
   imp.AddToCreditCardBalance(100);
}
finally {
   // Reset security state.
   imp.Revert();
}
```

El pseudocódigo siguiente muestra el patrón que puede usar para proteger el código y cumplir esta regla.

```csharp
try {
     try {
        // Do some work.
     }
     finally {
        // Reset security state.
     }
}
catch()
{
    throw;
}
```