---
title: Massenladen von verschlüsselten Daten in Spalten mithilfe von Always Encrypted
description: In diesem Artikel erfahren Sie, wie Sie mithilfe von Always Encrypted mit SQL Server ein Massenladen von Daten in Spalten ausführen.
ms.custom: seo-lt-2019
ms.date: 11/04/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Always Encrypted, bulk import
ms.assetid: b2ca08ed-a927-40fb-9059-09496752595e
author: jaszymas
ms.author: jaszymas
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 435c9e512278d3954c46e543ab6d68610f1cbdfc
ms.sourcegitcommit: 22e97435c8b692f7612c4a6d3fe9e9baeaecbb94
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92679258"
---
# <a name="bulk-load-encrypted-data-to-columns-using-always-encrypted"></a>Massenladen von verschlüsselten Daten in Spalten mithilfe von Always Encrypted
[!INCLUDE [SQL Server Azure SQL Database](../../../includes/applies-to-version/sql-asdb.md)]

Erstellen Sie den Benutzer mit der Option **ALLOW_ENCRYPTED_VALUE_MODIFICATIONS** , um verschlüsselte Daten zu laden, ohne während Massenkopiervorgängen auf dem Server Metadatenüberprüfungen durchzuführen. Diese Option soll von Legacytools oder Drittanbieter-ETL-Workflows (Extrahieren, Transformieren und Laden) verwendet werden, die Always Encrypted nicht verwenden können. Dadurch kann der Benutzer verschlüsselte Daten sicher von einem Tabellensatz mit verschlüsselten Spalten zu einem anderen Tabellensatz mit verschlüsselten Spalten (innerhalb derselben oder zu einer anderen Datenbank) verschieben.  

 ## <a name="the-allow_encrypted_value_modifications-option"></a>Die Option ALLOW_ENCRYPTED_VALUE_MODIFICATIONS  
 Sowohl [CREATE USER](../../../t-sql/statements/create-user-transact-sql.md) als auch [ALTER USER](../../../t-sql/statements/alter-user-transact-sql.md) verfügen über eine Option ALLOW_ENCRYPTED_VALUE_MODIFICATIONS. Wenn diese Option auf ON festgelegt wird (der Standardwert ist OFF), unterdrückt sie kryptografische Metadatenüberprüfungen bei Massenkopiervorgängen auf dem Server, wodurch der Benutzer verschlüsselte Daten zwischen Tabellen oder Datenbanken massenkopieren kann, ohne die Daten zu entschlüsseln.  
  
## <a name="data-migration-scenarios"></a>Datenmigrationsszenarien  
Die folgende Tabelle zeigt die empfohlenen Einstellungen für mehrere Migrationsszenarien.  
 
![Screenshot einer Tabelle mit den empfohlenen Einstellungen für mehrere Migrationsszenarios](../../../relational-databases/security/encryption/media/always-encrypted-migration.PNG "always-encrypted-migration")  

## <a name="bulk-loading-of-encrypted-data"></a>Massenladen von verschlüsselten Daten  
Verwenden Sie das folgende Verfahren, um verschlüsselte Daten zu laden.  

1.  Legen Sie die Option für den Benutzer in der Datenbank auf ON fest, der das Ziel für den Massenkopiervorgang darstellt. Beispiel:  
 
   ```  
    ALTER USER Bob WITH ALLOW_ENCRYPTED_VALUE_MODIFICATIONS = ON;  
   ```  

2.  Führen Sie Ihre Massenkopieranwendung oder Ihr Massenkopiertool aus, indem Sie als dieser Benutzer eine Verbindung herstellen. (Wenn Ihre Anwendung einen durch Always Encrypted aktivierten Clienttreiber verwendet, achten Sie darauf, dass die Verbindungszeichenfolge für die Datenquelle nicht **column encryption setting=enabled** enthält. Dadurch stellen Sie sicher, dass die von verschlüsselten Spalten abgerufenen Daten verschlüsselt bleiben. Weitere Informationen finden Sie unter [Entwickeln von Anwendungen mit Always Encrypted](always-encrypted-client-development.md).)  
  
3.  Legen Sie die Option ALLOW_ENCRYPTED_VALUE_MODIFICATIONS wieder auf OFF fest. Beispiel:  

    ```  
    ALTER USER Bob WITH ALLOW_ENCRYPTED_VALUE_MODIFICATIONS = OFF;  
    ```  

## <a name="potential-for-data-corruption"></a>Risiko der Datenbeschädigung  
Die falsche Verwendung dieser Option kann zur Datenbeschädigung führen. Die Option **ALLOW_ENCRYPTED_VALUE_MODIFICATIONS** ermöglicht es dem Benutzer, beliebige Daten in verschlüsselte Spalten in der Datenbank einzufügen. Dazu zählen auch Daten, die mit verschiedenen Schlüsseln, falsch oder überhaupt nicht verschlüsselt wurden. Wenn der Benutzer aus Versehen Daten kopiert, die nicht richtig mit dem für die Zielspalte festgelegten Verschlüsselungsschema (Spaltenverschlüsselungsschlüssel, Algorithmus, Verschlüsselungstyp) verschlüsselt wurden, können Sie diese Daten nicht entschlüsseln (die Daten sind beschädigt). Diese Option muss mit Vorsicht verwendet werden, da sie zur Datenbeschädigung in der Datenbank führen kann.  

Das folgende Szenario zeigt, wie nicht ordnungsgemäß importierte Daten zur Datenbeschädigung führen können:  

1.  Die Option ist für einen Benutzer auf ON festgelegt.  
 
2.  Der Benutzer führt die Anwendung aus, die mit der Datenbank verbunden ist. Die Anwendung verwendet Massen-APIs zum Einfügen von Klartextwerten in verschlüsselte Spalten. Die Anwendung erwartet von einem durch Always Encrypted aktivierten Clienttreiber die Verschlüsselung der Daten beim Einfügen. Die Anwendung ist jedoch falsch konfiguriert, sodass sie entweder einen Treiber verwendet, der Always Encrypted nicht unterstützt, oder die Verbindungszeichenfolge **column encryption setting=enabled** nicht enthält.  

3.  Die Anwendung sendet Klartextwerte an den Server. Da kryptografische Metadatenüberprüfungen auf dem Server für den Benutzer deaktiviert sind, lässt der Server zu, dass falsche Daten (Klartext statt richtig verschlüsselter Chiffretext) in eine verschlüsselte Spalte eingefügt werden.  
 
4.  Die gleiche oder eine andere Anwendung stellt mithilfe eines durch Always Encrypted aktivierten Treibers und mit **column encryption setting=enabled** in der Verbindungszeichenfolge eine Verbindung mit der Datenbank her und ruft die Daten ab. Die Anwendung erwartet, dass die Daten transparent entschlüsselt werden. Der Treiber kann die Daten jedoch nicht entschlüsseln, da es sich dabei um falschen Chiffretext handelt.  

## <a name="best-practice"></a>Bewährte Methode  
 
Verwenden Sie vorgesehene Benutzerkonten für Workloads mit langer Ausführungszeit, die diese Option verwenden.  
 
Legen Sie die Option bei Massenkopieranwendungen oder -tools, die verschlüsselte Daten ohne Entschlüsseln verschieben müssen, direkt vor dem Ausführen der Anwendung auf ON fest. Setzen Sie die Option sofort nach der Ausführung des Vorgangs auf OFF zurück.  
 
Verwenden Sie diese Option nicht zum Entwickeln neuer Anwendungen. Verwenden Sie stattdessen einen Clienttreiber, der eine API zum Unterdrücken kryptografischer Metadatenüberprüfungen für eine einzelne Sitzung bietet. Ein Beispiel hierfür ist die Option „AllowEncryptedValueModifications“ im .NET Framework-Datenanbieter für SQL Server. Weitere Informationen finden Sie unter [Kopieren verschlüsselter Daten mithilfe von SqlBulkCopy](develop-using-always-encrypted-with-net-framework-data-provider.md#copying-encrypted-data-using-sqlbulkcopy). 

## <a name="next-steps"></a>Nächste Schritte
- [Abfragen von Spalten mit Always Encrypted und SQL Server Management Studio](always-encrypted-query-columns-ssms.md)
- [Entwickeln von Anwendungen mit Always Encrypted](always-encrypted-client-development.md)

## <a name="see-also"></a>Weitere Informationen  
- [Always Encrypted](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)
- [Migrieren von Daten zu oder aus Spalten mithilfe von Always Encrypted mit dem SQL Server-Import/Export-Assistenten](always-encrypted-migrate-using-import-export-wizard.md)
- [CREATE USER &#40;Transact-SQL&#41;](../../../t-sql/statements/create-user-transact-sql.md)   
- [ALTER USER &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-user-transact-sql.md)   

