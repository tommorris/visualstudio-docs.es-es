---
title: 'Idiaenumsymbols:: Next | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Next method
ms.assetid: bfe5fe27-6a84-4392-910f-e325146d7552
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f419716901d35ea667f5e99a0c452d6e1b4d186c
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31459628"
---
# <a name="idiaenumsymbolsnext"></a>IDiaEnumSymbols::Next
Recupera un número especificado de símbolos en la secuencia de enumeración.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT Next (   
   ULONG        celt,  
   IDiaSymbol** rgelt,  
   ULONG*       pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 celt  
 [in] El número de símbolos en el enumerador que se va a recuperar.  
  
 rgelt  
 [out] Una matriz que se va a rellenar en con el [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objetos que representan los símbolos deseados.  
  
 pceltFetched  
 [out] Devuelve el número de símbolos en el enumerador capturado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si no hay ningún símbolo más. De lo contrario, devuelve un código de error.  
  
## <a name="example"></a>Ejemplo  
  
```C++  
IDiaEnumSymbols* pEnum  
CComPtr< IDiaSymbol> pSym;  
DWORD celt;  
pEnum->Next( 1, &pSym, &celt );  
```  
  
## <a name="see-also"></a>Vea también  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [Idiasession:: Findlinesbylinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)