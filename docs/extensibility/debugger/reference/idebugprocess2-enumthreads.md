---
title: IDebugProcess2::EnumThreads | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcess2::EnumThreads
helpviewer_keywords:
- IDebugProcess2::EnumThreads
ms.assetid: 05677385-7a7f-4545-8438-af00dde85db0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 786a3b4b5988b66e1fccc624154eeef67285ec84
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31116700"
---
# <a name="idebugprocess2enumthreads"></a>IDebugProcess2::EnumThreads
Recupera una lista de todos los subprocesos que se ejecutan en el proceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT EnumThreads(  
   IEnumDebugThreads2** ppEnum  
);  
```  
  
```csharp  
int EnumThreads(  
   out IEnumDebugThreads2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppEnum`  
 [out] Devuelve un [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md) objeto que contiene una lista de todos los subprocesos en todos los programas en el proceso.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Este método enumera los subprocesos que se ejecutan en cada programa y, a continuación, las combina en una vista de proceso de los subprocesos. Un único subproceso puede ejecutarse en varios programas; Este método enumera sólo una vez ese subproceso.  
  
 Este método presenta una lista de los subprocesos del proceso sin duplicados. En caso contrario, para enumerar los subprocesos que se ejecutan en un programa determinado, utilice la [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) método.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)