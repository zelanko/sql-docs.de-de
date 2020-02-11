---
title: Integration Services Parameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Integration Services, parameters
ms.assetid: b1bb3ea3-8097-4e76-b9c2-78a0f46a23bc
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 100e796bb27d1e60db000a364a0432273dd5cafb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66094234"
---
# <a name="integration-services-parameters"></a>Integration Services-Parameter
  Für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]können Sie sich entscheiden, Pakete [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] auf dem Computer zu analysieren, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] oder Paketdateien im Dateisystem. Wenn Sie sich dafür entscheiden, Dateien im Dateisystem zu analysieren, müssen Sie einen Pfad zum Ordner angeben, der die [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Pakete enthält.  
  
## <a name="options"></a>Tastatur  
 **SSIS-Pakete auf dem Computer analysieren**  
 Wählen Sie diese Option aus [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , um Pakete auf dem Computer zu analysieren. Standardmäßig ist diese Option ausgewählt.  
  
 **SSIS-Paketdateien analysieren**  
 Wählen Sie diese Option aus, um [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Pakete im Dateisystem zu analysieren.  
  
 **Pfad zu SSIS-Paketen**  
 Geben Sie einen UNC-Namen oder lokalen Pfad ein, unter dem sich die [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Pakete befinden. Sie müssen keine Dateinamen angeben. Wenn nicht auf den eingegebenen Pfad zugegriffen werden kann, können Sie nicht auf **weiter**klicken. Standardmäßig ist der Pfad leer. Dieses Feld ist nur aktiviert, wenn Sie **SSIS-Paketdateien analysieren**auswählen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Arbeiten mit Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md)   
 [Benutzeroberflächenreferenz des Upgrade Advisors](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)  
  
  
