---
title: GeneralFlags-Eigenschaft (ServerSettings)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- GeneralFlags Property (ServerSettings Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- GeneralFlags property
ms.assetid: 129bff8d-d2bc-4297-952f-d0a919d169f7
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: bd79263e09f1b3eccb4a4efff0ed8ecd036fcc9d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73659300"
---
# <a name="generalflags-property-serversettings-class"></a>GeneralFlags-Eigenschaft (ServerSettings-Klasse)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Ruft die allgemeinen Flags ab, die der Instanz [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]von zugeordnet sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.GeneralFlags [= value]  
```  
  
## <a name="parts"></a>Bestandteile  
 *Objekt*  
 Ein [ServerSettings-Klassenobjekt](../../../relational-databases/wmi-provider-configuration-classes/serversettings-class/serversettings-class.md) , das Servereinstellungen in einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]darstellt.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein Array von [ServerSettingsGeneralFlag-Klassenobjekten](../../../relational-databases/wmi-provider-configuration-classes/serversettingsgeneralflag-class/serversettingsgeneralflag-class.md) , das die allgemeinen, der Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]zugeordneten Flags angibt.  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren von Servernetzwerkprotokollen und Netzwerkbibliotheken](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
