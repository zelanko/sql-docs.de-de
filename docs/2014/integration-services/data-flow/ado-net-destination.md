---
title: ADO NET-Ziel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.adonetdest.f1
helpviewer_keywords:
- destinations [Integration Services], ADO.NET
- ADO.NET destination
ms.assetid: cb883990-d875-4d8b-b868-45f9f15ebeae
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 56f2a4d85579634c6e5d303c5cde8d766d162d42
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84916890"
---
# <a name="ado-net-destination"></a>ADO NET-Ziel
  Das ADO NET-Ziel lädt Daten in eine Reihe von [!INCLUDE[vstecado](../../includes/vstecado-md.md)]-kompatible Datenbanken, die eine Datenbanktabelle oder -sicht verwenden. Sie haben die Möglichkeit, diese Daten in eine vorhandene Tabelle oder Sicht zu laden, oder Sie können eine neue Tabelle erstellen und die Daten in die neue Tabelle laden.  
  
 Sie können mithilfe des ADO.NET-Ziels eine Verbindung mit [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] herstellen. Das Herstellen einer Verbindung mit [!INCLUDE[ssSDS](../../includes/sssds-md.md)] über OLE DB wird nicht unterstützt. Weitere Informationen zu [!INCLUDE[ssSDS](../../includes/sssds-md.md)] finden Sie unter [Azure SQL-Datenbank – Allgemeine Einschränkungen und Leitlinien](https://go.microsoft.com/fwlink/?LinkId=248228).  
  
## <a name="troubleshooting-the-ado-net-destination"></a>Problembehandlung des ADO NET-Ziels  
 Sie können die vom ADO NET-Ziel an externe Datenanbieter gerichteten Aufrufe protokollieren. Mithilfe dieser Protokollierungsfunktion können Sie Probleme beim Speichern von Daten in externen Datenquellen durch das ADO NET-Ziel behandeln. Aktivieren Sie zum Protokollieren der vom ADO NET-Ziel an externe Datenanbieter gerichteten Aufrufe die Paketprotokollierung, und wählen Sie das **Diagnostic** -Ereignis auf Paketebene aus. Weitere Informationen finden Sie unter [Behandeln von Problemen mit Paketausführungstools](../troubleshooting/troubleshooting-tools-for-package-execution.md).  
  
## <a name="configuring-the-ado-net-destination"></a>Konfigurieren des ADO NET-Ziels  
 Von diesem Ziel wird ein [!INCLUDE[vstecado](../../includes/vstecado-md.md)] -Verbindungs-Manager zum Herstellen einer Verbindung mit einer Datenquelle verwendet, und der Verbindungs-Manager gibt den zu verwendenden [!INCLUDE[vstecado](../../includes/vstecado-md.md)] -Anbieter an. Weitere Informationen finden Sie unter [ADO.NET Connection Manager](../connection-manager/ado-net-connection-manager.md).  
  
 Ein ADO NET-Ziel enthält Zuordnungen zwischen Eingabespalten und Spalten in der Zieldatenquelle. Sie müssen nicht allen Zielspalten eine Eingabespalten zuordnen. Die Eigenschaften einiger Zielspalten können jedoch die Zuordnung von Eingabespalten erfordern. Andernfalls könnten Fehler auftreten. Wenn z. B. eine Zielspalte keine NULL-Werte zulässt, muss dieser Zielspalte eine Eingabespalte zugeordnet werden. Darüber hinaus müssen die Datentypen zugeordneter Spalten kompatibel sein. Beispielsweise können Sie eine Eingabespalte mit einem string-Datentyp nicht einer Zielspalte mit einem numerischen Datentyp zuordnen, wenn der [!INCLUDE[vstecado](../../includes/vstecado-md.md)] -Anbieter diese Zuordnung nicht unterstützt.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt nicht das Einfügen von Text in Spalten mit dem Datentyp „image“. Weitere Informationen zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentypen finden Sie unter [Datentypen &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).  
  
> [!NOTE]  
>  Die Zuordnung einer Eingabespalte, deren Typ auf DT_DBTIME festgelegt ist, zu einer Datenbankspalte, deren Typ auf datetime festgelegt ist, wird vom ADO NET-Ziel nicht unterstützt. Weitere Informationen zu [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Datentypen finden Sie unter [Integration Services-Datentypen](integration-services-data-types.md).  
  
 Das ADO NET-Ziel weist eine reguläre Eingabe und eine Fehlerausgabe auf.  
  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Klicken Sie auf eines der folgenden Themen, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im Dialogfeld **ADO.NET-Ziel-Editor** festlegen können:  
  
-   [Ziel-Editor für ADO.NET &#40;Seite „Verbindungs-Manager“&#41;](../ado-net-destination-editor-connection-manager-page.md)  
  
-   [ADO.NET-Ziel-Editor &#40;Seite „Zuordnungen“&#41;](../ado-net-destination-editor-mappings-page.md)  
  
-   [Ziel-Editor für ADO.NET &#40;Seite „Fehlerausgabe“&#41;](../ado-net-destination-editor-error-output-page.md)  
  
 Das Dialogfeld **Erweiterter Editor** enthält die Eigenschaften, die programmgesteuert festgelegt werden können. Klicken Sie auf eines der folgenden Themen, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im Dialogfeld **Erweiterter Editor** oder programmgesteuert festlegen können:  
  
-   [Allgemeine Eigenschaften](../common-properties.md)  
  
-   [Benutzerdefinierte Eigenschaften von ADO.NET](ado-net-custom-properties.md)  
  
 Weitere Informationen zum Festlegen der Eigenschaften finden Sie unter [Festlegen der Eigenschaften einer Datenflusskomponente](set-the-properties-of-a-data-flow-component.md).  
  
  
