---
rank: 2
related_endpoints:
  - get_events
  - options_events
related_guides:
  - events/for-user
  - events/polling
  - events/pagination
required_guides: []
alias_paths: []
category_id: events
subcategory_id: null
is_index: false
id: events/for-enterprise
type: guide
total_steps: 5
sibling_id: events
parent_id: events
next_page_id: events/polling
previous_page_id: events/for-user
source_url: >-
  https://github.com/box/developer.box.com/blob/default/content/guides/events/for-enterprise.md
---
# エンタープライズイベントの取得

エンタープライズイベントを取得するには、管理者権限を持つユーザーを認証し、`stream_type`を`admin_logs`に設定して[`GET /events`](e://get_events) APIを呼び出します。

<Samples id="get_events" variant="enterprise">

</Samples>

<Message>

このAPIを使用するには、ユーザーは**新規レポートの実行と既存レポートへのアクセス**のための権限を持つ、会社の管理者または共同管理者である必要があります。

</Message>

## イベントタイプによるフィルタ

エンタープライズイベントフィードでは、イベントタイプによるフィルタがサポートされています。

<Samples id="get_events" variant="enterprise_filter">

</Samples>

イベントタイプの完全なリストについては、以下を参照してください。

## 制限

管理者イベントフィードでは、ロングポーリングがサポートされません。イベントに対するロングポーリングでは、ユーザーイベントフィードを使用します。

Boxでのイベントの保存は無期限ではありません。

ユーザーイベントは2週間から2か月間保存され、その後、保存されたユーザーイベントは削除されます。エンタープライズイベントには、APIを介した場合は1年間、Box管理コンソールのエクスポートされたレポート経由の場合は7年間アクセスできます。

このフィードでは、レイテンシよりも完全性を重視しています。つまり、Boxでは管理者イベントをユーザーフィードよりも高いレイテンシで配信することがあります。ユーザーイベントストリームとは違い、管理者イベントストリームでは、特定のイベントに対するフィルタが可能ですが、ロングポーリングはサポートされていません。

## イベントタイプ

エンタープライズに対して、以下のイベントがトリガーされます。

<!-- markdownlint-disable line-length -->

| イベント名                                          | 説明                                                                                                                                   |
| ---------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| `GROUP_ADD_USER`                               | ユーザーがグループに追加されました。                                                                                                                   |
| `NEW_USER`                                     | ユーザーが作成されました。                                                                                                                        |
| `GROUP_CREATION`                               | 新しいグループが作成されました。                                                                                                                     |
| `GROUP_DELETION`                               | グループが削除されました。                                                                                                                        |
| `DELETE_USER`                                  | ユーザーが削除されました。                                                                                                                        |
| `GROUP_EDITED`                                 | グループが編集されました。                                                                                                                        |
| `EDIT_USER`                                    | ユーザーが編集されました。                                                                                                                        |
| `GROUP_REMOVE_USER`                            | ユーザーがグループから削除されました。                                                                                                                  |
| `ADMIN_LOGIN`                                  | 管理者ログイン                                                                                                                              |
| `ADD_DEVICE_ASSOCIATION`                       | デバイスの関連付けが追加されました。                                                                                                                   |
| `CHANGE_FOLDER_PERMISSION`                     | フォルダに対する権限を編集します。                                                                                                                    |
| `FAILED_LOGIN`                                 | ログインに失敗しました。                                                                                                                         |
| `LOGIN`                                        | ログイン                                                                                                                                 |
| `REMOVE_DEVICE_ASSOCIATION`                    | デバイスの関連付けが削除されました。                                                                                                                   |
| `DEVICE_TRUST_CHECK_FAILED`                    | Device Trustチェックに失敗しました。                                                                                                             |
| `TERMS_OF_SERVICE_ACCEPT`                      | 利用規約が承諾されました。                                                                                                                        |
| `TERMS_OF_SERVICE_REJECT`                      | 利用規約が拒否されました。                                                                                                                        |
| `FILE_MARKED_MALICIOUS`                        | ファイルでウイルスが検出されました。イベントは、通知を希望した会社のみに送信されます。                                                                                          |
| `COPY`                                         | コピーされました。                                                                                                                            |
| `DELETE`                                       | 削除されました。                                                                                                                             |
| `DOWNLOAD`                                     | ダウンロードされました。                                                                                                                         |
| `EDIT`                                         | 編集されました。                                                                                                                             |
| `LOCK`                                         | ロックされました。                                                                                                                            |
| `MOVE`                                         | 移動されました。                                                                                                                             |
| `PREVIEW`                                      | プレビューされました。                                                                                                                          |
| `RENAME`                                       | ファイルまたはフォルダの名前または説明が変更されています。                                                                                                        |
| `STORAGE_EXPIRATION`                           | ファイルの自動削除が設定されました。                                                                                                                   |
| `UNDELETE`                                     | 復元されました。                                                                                                                             |
| `UNLOCK`                                       | ロックが解除されました。                                                                                                                         |
| `UPLOAD`                                       | アップロードされました。                                                                                                                         |
| `SHARE`                                        | 共有リンクが有効になりました。                                                                                                                      |
| `ITEM_SHARED_UPDATE`                           | 共有リンク設定が更新されました。                                                                                                                     |
| `UPDATE_SHARE_EXPIRATION`                      | 共有リンクの有効期限が延長されます。                                                                                                                   |
| `SHARE_EXPIRATION`                             | 共有リンクの有効期限が設定されました。                                                                                                                  |
| `UNSHARE`                                      | 共有リンクが削除されました。                                                                                                                       |
| `COLLABORATION_ACCEPT`                         | 招待が承認されました。                                                                                                                          |
| `COLLABORATION_ROLE_CHANGE`                    | ユーザーロールが変更されました。                                                                                                                     |
| `UPDATE_COLLABORATION_EXPIRATION`              | コラボレータの有効期限が延長されます。                                                                                                                  |
| `COLLABORATION_REMOVE`                         | コラボレータが削除されました。                                                                                                                      |
| `COLLABORATION_INVITE`                         | 招待されました。                                                                                                                             |
| `COLLABORATION_EXPIRATION`                     | コラボレータの有効期限が設定されました。                                                                                                                 |
| `EXTERNAL_COLLAB_SECURITY_SETTINGS`            | 外部コラボレーションのセキュリティ設定での変更                                                                                                              |
| `ITEM_SYNC`                                    | フォルダが同期されました。                                                                                                                        |
| `ITEM_UNSYNC`                                  | フォルダから同期対象のマークが解除されました。                                                                                                              |
| `ADD_LOGIN_ACTIVITY_DEVICE`                    | ユーザーがまだ確認されていないデバイスからログインしています。                                                                                                      |
| `REMOVE_LOGIN_ACTIVITY_DEVICE`                 | アプリに関連付けられたユーザーセッションが無効になりました。                                                                                                       |
| `USER_AUTHENTICATE_OAUTH2_ACCESS_TOKEN_CREATE` | OAuth 2.0アクセストークンが作成されました。                                                                                                           |
| `OAUTH2_ACCESS_TOKEN_REVOKE`                   | OAuth 2.0アクセストークンが取り消されました                                                                                                           |
| `CHANGE_ADMIN_ROLE`                            | ユーザーの管理者ロールが変更されたとき                                                                                                                  |
| `CONTENT_WORKFLOW_UPLOAD_POLICY_VIOLATION`     | 管理者が設定したアップロードポリシーをコラボレータが違反しました。                                                                                                    |
| `METADATA_INSTANCE_CREATE`                     | メタデータインスタンスの作成。                                                                                                                      |
| `METADATA_INSTANCE_UPDATE`                     | メタデータインスタンスの更新。                                                                                                                      |
| `METADATA_INSTANCE_DELETE`                     | メタデータインスタンスの削除。                                                                                                                      |
| `SHIELD_ALERT`                                 | 会社のShieldルールに基づいて、Shieldで異常なダウンロード、セッション、場所または悪意のあるコンテンツが検出されました。詳細については、[Shieldのアラートイベント](g://events/shield-alert-events)を参照してください。 |
| `TASK_ASSIGNMENT_UPDATE`                       | タスク割り当ての更新。                                                                                                                          |
| `TASK_ASSIGNMENT_CREATE`                       | タスク割り当てが作成されます。                                                                                                                      |
| `TASK_ASSIGNMENT_DELETE`                       | タスク割り当てが削除されます。                                                                                                                      |
| `TASK_CREATE`                                  | タスクが作成されます。                                                                                                                          |
| `TASK_UPDATE`                                  | タスクのコメントが編集されました。                                                                                                                    |
| `COMMENT_CREATE`                               | コメントがファイルに作成されます。                                                                                                                    |
| `COMMENT_DELETE`                               | ファイルのコメントが削除されます。                                                                                                                    |
| `GROUP_ADD_ITEM`                               | 項目がグループに追加されます。                                                                                                                      |
| `DATA_RETENTION_REMOVE_RETENTION`              | リテンションが削除されます。                                                                                                                       |
| `DATA_RETENTION_CREATE_RETENTION`              | リテンションが作成されます。                                                                                                                       |
| `RETENTION_POLICY_ASSIGNMENT_ADD`              | リテンションポリシー割り当てが追加されます。                                                                                                               |
| `LEGAL_HOLD_ASSIGNMENT_CREATE`                 | リーガルホールドの割り当てが作成されます。                                                                                                                |
| `LEGAL_HOLD_ASSIGNMENT_DELETE`                 | リーガルホールドの割り当てが削除されます。                                                                                                                |
| `LEGAL_HOLD_POLICY_CREATE`                     | リーガルホールドポリシーが作成されます。                                                                                                                 |
| `LEGAL_HOLD_POLICY_UPDATE`                     | リーガルホールドポリシーが更新されます。                                                                                                                 |
| `LEGAL_HOLD_POLICY_DELETE`                     | リーガルホールドポリシーが削除されます。                                                                                                                 |
| `CONTENT_WORKFLOW_SHARING_POLICY_VIOLATION`    | 共有ポリシー違反があります。                                                                                                                       |
| `APPLICATION_PUBLIC_KEY_ADDED`                 | アプリケーションの公開キーが追加されます。                                                                                                                |
| `APPLICATION_PUBLIC_KEY_DELETED`               | アプリケーションの公開キーが削除されます。                                                                                                                |
| `APPLICATION_CREATED`                          | Box開発者コンソールで新しいアプリケーションが作成されました。                                                                                                     |
| `CONTENT_WORKFLOW_POLICY_ADD`                  | コンテンツポリシーが追加されます。                                                                                                                    |
| `CONTENT_WORKFLOW_AUTOMATION_ADD`              | 自動化が追加されます。                                                                                                                          |
| `CONTENT_WORKFLOW_AUTOMATION_DELETE`           | 自動化が削除されます。                                                                                                                          |
| `EMAIL_ALIAS_CONFIRM`                          | ユーザーのメールエイリアスが確認されます。                                                                                                                |
| `EMAIL_ALIAS_REMOVE`                           | ユーザーのメールエイリアスが削除されます。                                                                                                                |
| `WATERMARK_LABEL_CREATE`                       | 電子すかしがファイルに追加されます。                                                                                                                   |
| `WATERMARK_LABEL_DELETE`                       | 電子すかしがファイルから削除されます。                                                                                                                  |
| `ACCESS_GRANTED`                               | ユーザーが自分のアカウントに対するBoxのアクセス権限を付与しました。                                                                                                  |
| `ACCESS_REVOKED`                               | ユーザーが自分のアカウントに対するBoxアクセス権限を取り消しました。                                                                                                  |
| `METADATA_TEMPLATE_CREATE`                     | メタデータテンプレートインスタンスの作成。                                                                                                                |
| `METADATA_TEMPLATE_UPDATE`                     | メタデータテンプレートインスタンスの更新。                                                                                                                |
| `METADATA_TEMPLATE_DELETE`                     | メタデータテンプレートインスタンスの削除。                                                                                                                |
| `ITEM_OPEN`                                    | 項目が開かれました。                                                                                                                           |
| `ITEM_MODIFY`                                  | 項目が変更されました。                                                                                                                          |
| `CONTENT_WORKFLOW_ABNORMAL_DOWNLOAD_ACTIVITY`  | 管理コンソールで設定されたポリシーがトリガーされたとき。                                                                                                         |
| `GROUP_REMOVE_ITEM`                            | 管理コンソールでフォルダがグループから削除されました。                                                                                                          |
| `GROUP_ADD_ITEM`                               | 管理コンソールでフォルダがグループに追加されました。                                                                                                           |
| `FILE_WATERMARKED_DOWNLOAD`                    | 電子すかし付きファイルがダウンロードされました。                                                                                                             |
| `ENTERPRISE_APP_AUTHORIZATION_UPDATE`          | JWTアプリケーションが承認または再承認されました                                                                                                            |

<!-- markdownlint-enable line-length -->

## 匿名ユーザー

場合によっては、イベントフィードには、IDが`2`のユーザーが表示される可能性があります。これは、匿名ユーザーを表すBoxの内部識別子です。

匿名ユーザーは、ログインしていないユーザーです。この状況は、ユーザーがコンテンツを操作し、最初にログインを求められない場合にいつでも発生する可能性があります。たとえば、ユーザーが、公開共有リンクを使用してファイルをダウンロードするときなどです。
