# 第6回 解答

## 演習

<!-- [tool call] の行は、表示された行をそのまま貼り付けてください。終わらなかった STEP は、空欄のままでかまいません。 -->

- STEP 1 のツールの名前：search_materials
- STEP 2 の [tool call]：glossary_search_glossary({'query': '3レベル'}
- STEP 3 の [tool call]：fetch_fetch({'url': 'https://modelcontextprotocol.io/'}
- STEP 4 の [tool call]： aws_aws___search_documentation({'topics': ['general'], 'search_phrase': 'Versioning S3 what is it Amazon Simple Storage Service'}
aws_aws___search_documentation({'search_phrase': 'Amazon S3 バージョニング 概要', 'topics': ['general']}
- 気づき・疑問：
MCPサーバに接続するものを増やす分、モデルの応答回数も増えていった。


## 宿題

<!-- 基礎・実装・発展のどれか1つに取り組めば完了です。 -->

- 取り組んだレベル：実装 
- やったこと：MCPサーバにmake_quizを追加した
return json.dumps(
            {"error": f"第{lecture}回の用語は見つかりません。用語がある回: {lectures}"},
            ensure_ascii=False,
        )
をquizに実装し、問題を作れないと分かりやすいようにした

uv run python -m app.mcp_agent --trace "第2回の確認問題を1問出して"

----
範囲外の引数で変えるメッセージ
uv run python -m app.mcp_agent --trace "第99回のクイズを作って"
----
- 結果：
[tools] MCP サーバー（app/mcp_servers.json）
第2回からの確認問題です！

**問：**「QLoRA」の意味は？

ぜひ考えてみてくださいね！回答のヒントや、わからない部分があればいつでも質問してください。

（関連する回：第2回）

--- trace ---
[tool call]   glossary_make_quiz({'lecture': 2})

-------
[tools] MCP サーバー（app/mcp_servers.json）
AIエンジニアリング講座（AIE2026）の用語集を確認したところ、第99回という回は設定されておりません。

現在、用語やクイズが用意されているのは以下の回となっています：
- 第1回
- 第2回
- 第3回
- 第4回
- 第6回

もしよろしければ、上記のいずれかの回の確認問題を作成いたしますので、ご希望の回を指定してください！

--- trace ---
[tool call]   glossary_make_quiz({'lecture': 99})

- 気づき・疑問：
引数が範囲外のときのメッセージで、コードで制御しているため正しくメッセージを書くことが出来た
またクイズが用意できる回も明記できているためよい設計になったのではないかと考える
