## Gym, 20 ##

##### Note : Site yang disediakan oleh tjctf sudah mati #####

Soal :

`Aneesh wants to acquire a summer bod for beach week, but time is running out. Can you help him create a plan to attain his goal?`

`nc p1.tjctf.org 8008`

Maksud dari soal adalah, dari 4 pilihan yang disediakan, kita harus bisa mendapatkan value yang pas untuk turun dari 211 ke 180, yaitu 31.

Melihat source code nya, ada 4 nilai yaitu `-1,-2,-3, dan -4`. Kita membutuhkan `31` untuk mencapai goal kitam padahal nilai terbesar hanya 4, sedangkan `4 x 7 = 28`.

Export `gym` ke `gym.c` dengan menggunakan `hydra`. Dilihat dari fungsi ini :

```c
    if (iVar1 == 2) {
      iVar1 = do_pushup((ulong)local_a8);
      local_ac = local_ac - iVar1;
    }
    else {
      if (iVar1 < 3) {
        if (iVar1 == 1) {
          iVar1 = eat_healthy((ulong)local_a8);
          local_ac = local_ac - iVar1;
        }
      }
      else {
        if (iVar1 == 3) {
          iVar1 = go_run((ulong)local_a8);
          local_ac = local_ac - iVar1;
        }
        else {
          if (iVar1 != 4) goto LAB_00100b5d;
        }
        iVar1 = go_sleep((ulong)local_a8);
        local_ac = local_ac - iVar1;
      }
    }
LAB_00100b5d:
    local_a8 = local_a8 + 1;
  } while( true );
}
```
Kode yang sudah saya simpulkan :

```c
if (iVar1 == 2) {
  weight = weight - 1;
}
else {
  if (iVar1 < 3) {
    if iVar1 == 1) {
      weight = weight - 3;
    }
  }
}
else {
  if (iVar1 = 3) {
    weight = weight -2;
  }
  else {
    if (iVar1 != 4) {
      counter = counter + 1;
    }
  }
}
```

Bisa dilihat bahwa jika kita pilih 2, weight akan berkurang 1. Jika input kita tidak 2,  maka akan masuk ke else selanjutnya. Jika input kita 3, kurangi 2. Jika tidak, akan masuk ke else selanjutnya. Jika input tidak 4, counter akan naik 1.

Saya lihat bahwa ada satu hal yang aneh dari loop ini, yaitu kita selalu mengurangi `2 + 3` jika kita melakukan 3.

Setelah ini cukup simpel, tinggal lakukan `3 6 kali (6 * 5 = 30)` lalu lakukan `2 untuk menambah 1`.

Flag : `tjctf{w3iGht_l055_i5_d1ff1CuLt}`
