---
title: 'Idiadatasource:: Loaddatafrompdb | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataFromPdb method
ms.assetid: 02159073-8144-47f8-a0b0-aa0edcb92b5b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1910d54ad1a9d2964869beb4854ea97600569b7c
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31468364"
---
# <a name="idiadatasourceloaddatafrompdb"></a>IDiaDataSource::loadDataFromPdb
Se abre y se prepara un archivo de programa (.pdb) de la base de datos como un origen de datos de depuración.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT loadDataFromPdb (  
   LPCOLESTR pdbPath  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 pdbPath  
 [in] La ruta de acceso al archivo .pdb.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error. La tabla siguiente muestran los posibles valores devueltos para este método.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|E_PDB_NOT_FOUND|No se pudo abrir el archivo, o si se determina que el archivo tiene un formato no válido.|  
|E_PDB_FORMAT|Se ha intentado obtener acceso a un archivo con un formato obsoleto.|  
|E_INVALIDARG|Parámetro no válido.|  
|E_UNEXPECTED|Ya se ha preparado el origen de datos.|  
  
## <a name="remarks"></a>Comentarios  
 Este método carga los datos de depuración directamente desde un archivo PDB.  
  
 Para validar el archivo .pdb en criterios específicos, utilice la [idiadatasource:: Loadandvalidatedatafrompdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) método.  
  
 Para obtener acceso a los procesos de carga de datos (a través de un mecanismo de devolución de llamada), use la [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) método.  
  
 Para cargar un archivo .pdb directamente desde la memoria, utilice la [idiadatasource:: Loaddatafromistream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) método.  
  
## <a name="example"></a>Ejemplo  
  
```C++  
HRESULT hr = pSource->loadDataFromPdb( L"myprog.pdb" );  
if (FAILED(hr))  
{  
    // report error  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [Idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [Idiadatasource:: Loadandvalidatedatafrompdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)