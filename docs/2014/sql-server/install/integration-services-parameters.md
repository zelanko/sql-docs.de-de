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
ms.openlocfilehash: 76a5ebe7018fdc58f02a4d2454d40f172c752c4e
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059270"
---
# <a name="integration-services-parameters"></a>Integration Services-Parameter
  Für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] können Sie sich entscheiden, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Pakete auf dem Computer zu analysieren, oder [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Paketdateien im Dateisystem. Wenn Sie sich dafür entscheiden, Dateien im Dateisystem zu analysieren, müssen Sie einen Pfad zum Ordner angeben, der die [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Pakete enthält.  
  
## <a name="options"></a>Optionen  
 **SSIS-Pakete auf dem Computer analysieren**  
 Wählen Sie diese Option aus, um [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Pakete auf dem Computer zu analysieren. Diese Option ist standardmäßig ausgewählt.  
  
 **SSIS-Paketdateien analysieren**  
 Wählen Sie diese Option aus, um [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Pakete im Dateisystem zu analysieren.  
  
 **Pfad zu SSIS-Paketen**  
 Geben Sie einen UNC-Namen oder lokalen Pfad ein, unter dem sich die [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Pakete befinden. Sie müssen keine Dateinamen angeben. Wenn nicht auf den eingegebenen Pfad zugegriffen werden kann, können Sie nicht auf **weiter**klicken. Standardmäßig ist der Pfad leer. Dieses Feld ist nur aktiviert, wenn Sie **SSIS-Paketdateien analysieren**auswählen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Arbeiten mit Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md)   
 [Benutzeroberflächenreferenz des Upgrade Advisors](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)  
  
  
