---
title: IDebugComPlusSymbolProvider2::GetTypesByName | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetTypesByName
- IDebugComPlusSymbolProvider2::GetTypesByName
ms.assetid: ef76b1a8-6910-48fe-b4af-d9045eefd23f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 098c04615629b844fae8022058d47455db9cd98a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31104282"
---
# <a name="idebugcomplussymbolprovider2gettypesbyname"></a>IDebugComPlusSymbolProvider2::GetTypesByName
Recupera un tipo dado su nombre.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetTypesByName(  
   LPCOLESTR          pszClassName,  
   NAME_MATCH         nameMatch,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int GetTypesByName(  
   string               pszClassName,  
   enum_ NAME_MATCH     nameMatch,  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pszClassName`  
 [in] Nombre del tipo.  
  
 `nameMatch`  
 [in] Selecciona el tipo de coincidencia, por ejemplo, distingue mayúsculas de minúsculas. Un valor de la [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) enumeración.  
  
 `ppEnum`  
 [out] Un enumerador que contiene el tipo o tipos con el nombre especificado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Para los tipos genéricos, el nombre para buscar una "lista\<int >' o ' lista\<int, int >' sería"List". Si los tipos del mismo nombre aparecen en varios módulos, el `ppEnum` parámetro contendrá todas las copias. Tiene que usar [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) y distinguir en función de la `guidModule` parámetro.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo implementar este método para un **CDebugSymbolProvider** objeto que expone la [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md) interfaz.  
  
```cpp  
HRESULT CDebugSymbolProvider::GetTypesByName(  
    LPCOLESTR pszClassName,  
    NAME_MATCH nameMatch,  
    IEnumDebugFields** ppEnum  
)  
{  
    HRESULT hr = S_OK;  
    CModIter ModIter;  
    CModule* pmodule; // the iterator owns the reference  
    CFieldList listField;  
  
    ASSERT(IsValidWideStringPtr(pszClassName));  
    ASSERT(IsValidWritePtr(ppEnum, IEnumDebugFields*));  
  
    METHOD_ENTRY( CDebugSymbolProvider::GetTypesByName );  
  
    IfFalseGo( pszClassName && ppEnum, E_INVALIDARG );  
    *ppEnum = NULL;  
  
    IfFailGo( GetModuleIter(&ModIter) );  
  
    hr = S_FALSE;  
  
    if ( nameMatch == nmCaseInsensitive)  
    {  
        while (ModIter.GetNext(&pmodule))  
        {  
            if (pmodule->FindTypesByNameCaseInsensitive( pszClassName,  
                    &listField,  
                    this ) )  
            {  
                hr = S_OK;  
            }  
        }  
    }  
    else  
    {  
        while (ModIter.GetNext(&pmodule))  
        {  
            if (pmodule->FindTypesByName( pszClassName,  
                                          &listField,  
                                          this) )  
            {  
                hr = S_OK;  
            }  
        }  
    }  
  
    // If the list is empty then no type  
    IfFalseGo( listField.GetCount(), E_FAIL );  
  
    // Create enumerator  
    IfFailGo( CreateEnumerator( ppEnum, &listField ) );  
  
Error:  
  
    METHOD_EXIT( CDebugSymbolProvider::GetTypesByName, hr );  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)