---
title: MemoryTypeEnum | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MemoryTypeEnum enumeration
ms.assetid: 8778c047-edeb-4495-8f9f-3f8bbb297099
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 616bae99a4cb3ffafa4cdf773bce63576ed04e7a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31469599"
---
# <a name="memorytypeenum"></a>MemoryTypeEnum
Especifica el tipo de memoria para tener acceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
enum MemoryTypeEnum {  
   MemTypeCode,  
   MemTypeData,  
   MemTypeStack,  
   MemTypeAny = -1  
};  
```  
  
#### <a name="parameters"></a>Parámetros  
 `MemTypeCode`  
 Tiene acceso a código sólo de memoria.  
  
 `MemTypeData`  
 Tiene acceso a datos o la pila de la memoria.  
  
 `MemTypeStack`  
 Tiene acceso a la pila solo memoria.  
  
 `MemTypeAny`  
 Tiene acceso a cualquier tipo de memoria.  
  
## <a name="remarks"></a>Comentarios  
 Los valores de esta enumeración se pasan a la [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md) método para limitar el acceso a diferentes tipos de memoria.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: cvconst.h  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)