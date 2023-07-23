# passwordGenerator-streamlit
```python
import streamlit as st
import random
import string

# 必要な変数
alphabet = string.ascii_letters

# タイトル
st.header("パスワード生成機")

# パスワードの長さをスライダーで指定
password_length = st.slider("パスワードの長さ", min_value=1, max_value=30, value=10, step=1)

# アルファベットを入れるかどうか
abcCb = st.checkbox(label="アルファベットを含む")

# 数字を入れるかどうか
numCb = st.checkbox(label="数字を含む")

# 記号を入れるかどうか
symCb = st.checkbox(label="記号を含む")

selected_chars = ''  # selected_charsを初期化

# 生成
if st.button(label="生成"):
    if abcCb:
        selected_chars += string.ascii_letters
    if numCb:
        selected_chars += string.digits
    if symCb:
        selected_chars += string.punctuation

    if not selected_chars:
        # selected_charsが空の場合の処理
        password = "チェックボックス：少なくとも1つ選択してください。"
    else:
        password = ''.join(random.choice(selected_chars) for _ in range(password_length))
    
    st.text_area("生成されたパスワード", value=password, key="password_input")

```
