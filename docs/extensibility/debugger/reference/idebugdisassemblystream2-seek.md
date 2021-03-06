---
title: IDebugDisassemblyStream2::Seek | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDisassemblyStream2::Seek
helpviewer_keywords:
- IDebugDisassemblyStream2::Seek
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 55a8c2c205627130e8dd6dd28f288b2d3dee9d2e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31103596"
---
# <a name="idebugdisassemblystream2seek"></a>IDebugDisassemblyStream2::Seek
Mueve el puntero de lectura en la secuencia de desensamblado un número determinado de instrucciones con respecto a una posición especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT Seek(   
   SEEK_START          dwSeekStart,  
   IDebugCodeContext2* pCodeContext,  
   UINT64              uCodeLocationId,  
   INT64               iInstructions  
);  
```  
  
```csharp  
int Seek(   
   enum_SEEK_START    dwSeekStart,  
   IDebugCodeContext2 pCodeContext,  
   ulong              uCodeLocationId,  
   long               iInstructions  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwSeekStart`  
 [in] Un valor de la [SEEK_START](../../../extensibility/debugger/reference/seek-start.md) enumeración que especifica la posición relativa para iniciar el proceso de búsqueda.  
  
 `pCodeContext`  
 [in] El [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) objeto que representa el contexto del código que la operación de búsqueda es relativa a. Este parámetro se utiliza sólo si `dwSeekStart`  =  `SEEK_START_CODECONTEXT`; en caso contrario, este parámetro se pasa por alto y puede ser un valor null.  
  
 `uCodeLocationId`  
 [in] El identificador de ubicación del código que la operación de búsqueda es relativa a. Este parámetro se utiliza si `dwSeekStart`  =  `SEEK_START_CODELOCID`; en caso contrario, este parámetro se omite y se puede establecer en 0. Vea la sección Comentarios para el [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) método para obtener una descripción de un identificador de ubicación del código.  
  
 `iInstructions`  
 [in] El número de instrucciones para mover con respecto a la posición especificada en `dwSeekStart`. Este valor puede ser negativo para moverse hacia atrás.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si se hizo la posición de búsqueda a un punto más allá de la lista de instrucciones disponibles. De lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Si la búsqueda se realizó en una posición antes del comienzo de la lista, se establece la posición de lectura en la primera instrucción en la lista. Si el vea consistía en una posición después del final de la lista, la posición de lectura se establece a la última instrucción en la lista.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [SEEK_START](../../../extensibility/debugger/reference/seek-start.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)