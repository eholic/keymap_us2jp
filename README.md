# keymap_us2jp

QMKで日本語配列キーボードを英語配列のように使うキーコード。

## 準備
レポジトリ内のファイルをkeymapにコピーして、以下の変更をする。

- rules.mk
```makefile
SRC += us2jp.c
```

- keymap.c
ヘッダ読み込み。
```c
#include "keymap_jp.h"
#include "keymap_us2jp.h"
```

`process_record_user`内で、`us2jp`を呼ぶ。
```c
bool process_record_user(uint16_t keycode, keyrecord_t *record) {
  return us2jp(keycode, record);
}
```

## キーコード
キーマップ定義の時に、`JP_***`の代わりに、[keymap_us2jp.h](keymap_us2jp.h)で定義されている`UJ_***`を使う。
> `SAFE_RANGE`を使っているので、別のカスタムキーコードを定義する場合は、`NEW_SAFE_RANGE`を使うこと。

- 定義済みキーコード
> UJ_2, UJ_6, UJ_7, UJ_8, UJ_9, UJ_0, UJ_MINS, UJ_EQL, UJ_SCLN, UJ_QUOT, UJ_GRV
