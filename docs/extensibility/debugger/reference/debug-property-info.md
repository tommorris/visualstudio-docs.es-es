---
title: DEBUG_PROPERTY_INFO | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DEBUG_PROPERTY_INFO
helpviewer_keywords:
- DEBUG_PROPERTY_INFO structure
ms.assetid: 5a085d18-62c6-4740-b9e9-3f5db6bfdf7f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4466d74d0e19b898b3c377c67a14f7c39922d915
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31103466"
---
# <a name="debugpropertyinfo"></a>DEBUG_PROPERTY_INFO
Contiene información sobre una propiedad de depuración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
typedef struct tagDEBUG_PROPERTY_INFO {   
   DEBUGPROP_INFO_FLAGS dwValidFields;  
   BSTR                 bstrFullName;  
   BSTR                 bstrName;  
   BSTR                 bstrType;  
   BSTR                 bstrValue;  
   IDebugProperty2*     pProperty;  
   DBG_ATTRIB_FLAGS     dwAttrib;  
} DEBUG_PROPERTY_INFO;  
```  
  
```csharp  
public struct DEBUG_PROPERTY_INFO {   
   public uint            dwValidFields;  
   public string          bstrFullName;  
   public string          bstrName;  
   public string          bstrType;  
   public string          bstrValue;  
   public IDebugProperty2 pProperty;  
   public ulong           dwAttrib;  
};  
```  
  
## <a name="members"></a>Miembros  
 dwValidFields  
 Una combinación de indicadores de la [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) enumeración que especifica qué campos se rellenen.  
  
 bstrFullName  
 Nombre completo de la propiedad.  
  
 bstrName  
 El nombre de propiedad dentro de un contexto.  
  
 bstrType parámetro  
 El tipo de propiedad como una cadena con formato.  
  
 bstrValue parámetro  
 El valor de propiedad como una cadena con formato.  
  
 pProperty  
 El [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) objeto descrito por esta estructura.  
  
 dwAttrib  
 Una combinación de indicadores de la [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) enumeración que describe los atributos de esta propiedad.  
  
## <a name="remarks"></a>Comentarios  
 Una propiedad es un objeto de una naturaleza jerárquica que tiene un nombre, tipo y valor. Por ejemplo, puede describir una propiedad de las variables locales, parámetros, variables de inspección y expresiones y registros.  
  
 Esta estructura se pasa a la [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) método donde se rellena. Esta estructura también se devuelve como parte de una lista de esta estructura de la [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) interfaz que, a su vez, se devuelve de una llamada a la [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) y [ EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) métodos.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)