---
title: Replizieren von Daten in verschlüsselten Spalten (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- encryption [SQL Server], replicating data
- encryption [SQL Server replication]
- publishing [SQL Server replication], encrypted columns
ms.assetid: d1f8f586-e5a3-4a71-9391-11198d42bfa3
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 00bec2a06d024b4c1482b0e9865c58ea6d1e985d
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52766152"
---
# <a name="replicate-data-in-encrypted-columns-sql-server-management-studio"></a>Replizieren von Daten in verschlüsselten Spalten (SQL Server Management Studio)
  Mithilfe der Replikation können Sie verschlüsselte Spaltendaten veröffentlichen. Zum Entschlüsseln und Verwenden dieser Daten auf dem Abonnenten muss der zum Verschlüsseln der Daten auf dem Verleger verwendete Schlüssel auch auf dem Abonnenten vorhanden sein. Die Replikation bietet keinen sicheren Mechanismus zum Transportieren von Verschlüsselungsschlüsseln. Sie müssen den Verschlüsselungsschlüssel auf dem Abonnenten manuell neu erstellen. In diesem Thema wird veranschaulicht, wie Sie eine Spalte auf dem Verleger verschlüsseln und wie Sie sicherstellen, dass der Verschlüsselungsschlüssel auf dem Abonnenten verfügbar ist.  
  
 Dazu müssen die folgenden grundlegenden Schritte ausgeführt werden:  
  
1.  Erstellen Sie den symmetrischen Schlüssel auf dem Verleger.  
  
2.  Verschlüsseln Sie Spaltendaten mit dem symmetrischen Schlüssel.  
  
3.  Veröffentlichen Sie die Tabelle mit der verschlüsselten Spalte.  
  
4.  Abonnieren Sie die Veröffentlichung.  
  
5.  Initialisieren Sie das Abonnement.  
  
6.  Erstellen Sie den symmetrischen Schlüssel auf dem Abonnenten neu, indem Sie für ALGORITHM, KEY_SOURCE und IDENTITY_VALUE dieselben Werte wie in Schritt 1 verwenden.  
  
7.  Greifen Sie auf die verschlüsselten Spaltendaten zu.  
  
> [!NOTE]  
>  Verwenden Sie zum Verschlüsseln von Spaltendaten einen symmetrischen Schlüssel. Der symmetrische Schlüssel kann auf unterschiedliche Weise auf dem Verleger und dem Abonnenten gesichert werden.  
  
### <a name="to-create-and-replicate-encrypted-column-data"></a>So erstellen und replizieren Sie verschlüsselte Spaltendaten  
  
1.  Führen Sie [CREATE SYMMETRIC KEY](/sql/t-sql/statements/create-symmetric-key-transact-sql)auf dem Verleger aus.  
  
    > [!IMPORTANT]  
    >  Der Wert von KEY_SOURCE stellt wichtige Daten dar, die verwendet werden können, um den symmetrischen Schlüssel neu zu erstellen und Daten zu entschlüsseln. KEY_SOURCE muss immer sicher gespeichert und transportiert werden.  
  
2.  Führen Sie [OPEN SYMMETRIC KEY](/sql/t-sql/statements/open-symmetric-key-transact-sql) aus, um den neuen Schlüssel zu öffnen.  
  
3.  Verwenden Sie die [EncryptByKey](/sql/t-sql/functions/encryptbykey-transact-sql) -Funktion, um Spaltendaten auf dem Verleger zu verschlüsseln.  
  
4.  Führen Sie [CLOSE SYMMETRIC KEY](/sql/t-sql/statements/close-symmetric-key-transact-sql) aus, um den Schlüssel zu schließen.  
  
5.  Veröffentlichen Sie die Tabelle, die die verschlüsselte Spalte enthält. Weitere Informationen finden Sie unter [Create a Publication](../publish/create-a-publication.md).  
  
6.  Abonnieren Sie die Veröffentlichung. Weitere Informationen finden Sie unter [Erstellen eines Pullabonnnements](../create-a-pull-subscription.md) und [Erstellen eines Pushabonnements](../create-a-push-subscription.md).  
  
7.  Initialisieren Sie das Abonnement. Weitere Informationen finden Sie unter [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).  
  
8.  Führen Sie auf dem Abonnenten [CREATE SYMMETRIC KEY](/sql/t-sql/statements/create-symmetric-key-transact-sql) aus, indem Sie für ALGORITHM, KEY_SOURCE und IDENTITY_VALUE die gleichen Werte wie in Schritt 1 verwenden. Für ENCRYPTION BY können Sie einen anderen Wert angeben.  
  
    > [!IMPORTANT]  
    >  Der Wert von KEY_SOURCE stellt wichtige Daten dar, die verwendet werden können, um den symmetrischen Schlüssel neu zu erstellen und Daten zu entschlüsseln. KEY_SOURCE muss immer sicher gespeichert und transportiert werden.  
  
9. Führen Sie [OPEN SYMMETRIC KEY](/sql/t-sql/statements/open-symmetric-key-transact-sql) aus, um den neuen Schlüssel zu öffnen.  
  
10. Verwenden Sie die [DecryptByKey](/sql/t-sql/functions/decryptbykey-transact-sql) -Funktion, um replizierte Daten auf dem Verleger zu entschlüsseln.  
  
11. Führen Sie [CLOSE SYMMETRIC KEY](/sql/t-sql/statements/close-symmetric-key-transact-sql) aus, um den Schlüssel zu schließen.  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel werden ein symmetrischer Schlüssel, ein Zertifikat zum Sichern des symmetrischen Schlüssels und ein Hauptschlüssel erstellt. Diese Schlüssel werden in der Veröffentlichungsdatenbank erstellt. Sie werden dann verwendet, um eine verschlüsselte Spalte (EncryptedCreditCardApprovalCode) in der `SalesOrderHeader` -Tabelle zu erstellen. Diese Spalte wird in der AdvWorksSalesOrdersMerge-Veröffentlichung anstelle der nicht verschlüsselten CreditCardApprovalCode-Spalte veröffentlicht. Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Anmeldeinformationen zur Laufzeit anzugeben. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden müssen, muss die Datei an einem sicheren Ort gespeichert werden, um unberechtigten Zugriff zu vermeiden.  
  
 [!code-sql[HowTo#sp_PublishEncryptedColumn](../../../snippets/tsql/SQL15/replication/howto/tsql/publishencryptedcolumn.sql#sp_publishencryptedcolumn)]  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepub.sql#sp_addmergearticle)]  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird derselbe symmetrische Schlüssel in der Abonnementdatenbank mithilfe derselben Werte für ALGORITHM, KEY_SOURCE und IDENTITY_VALUE aus dem ersten Beispiel neu erstellt. Bei diesem Beispiel wird davon ausgegangen, dass Sie bereits ein Abonnement der AdvWorksSalesOrdersMerge-Veröffentlichung initialisiert haben, um die verschlüsselte Spalte zu replizieren. Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Anmeldeinformationen zur Laufzeit anzugeben. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden müssen, muss die Datei während des Speicherns und des Transports gesichert werden, um unberechtigten Zugriff zu vermeiden.  
  
 [!code-sql[HowTo#sp_SubscriberEncryptedColumn](../../../snippets/tsql/SQL15/replication/howto/tsql/subscriberencryptedcolumn.sql#sp_subscriberencryptedcolumn)]  
  
## <a name="see-also"></a>Siehe auch  
 [Sicherheitsübersicht &#40;Replikation&#41;](security-overview-replication.md)   
 [Erstellen identischer symmetrischer Schlüssel auf zwei Servern](../../security/encryption/create-identical-symmetric-keys-on-two-servers.md)  
  
  
