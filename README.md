# Supported cars
✅ means Seatbelt is not needed (Only for AVN-ZX02i afaik)

💺 means Seatbelt is needed.

📝 means Seatbelt support is planned.

🚧 means Seatbelt is working on support.

❌ means Seatbelt does not have support.

| Manufacturer | Model   | Year/Version | State  |
| ------------ | ------- | ------------ | ------ |
| Denso-ten    | ECLIPSE | AVN-ZX02i    | ✅     |
# Save
~~For some reason, it seems cartridges come with saves. If there is no save on the cart, we recieve an error known as Error 3.~~
Kuruma de DS can't load data on emulators, causing error 3.
Here are the other errors
## Save Errors
| ID  | String ID                       | Cause       |
| --- | ------------------------------- | ----------- |
| 1   | `GAMESAVE_ERR_CARD_CONNECT`     | Unknown     |
| 2   | `GAMESAVE_ERR_SAVE_OTHER`       | Unknown     |
| 3   | `GAMESAVE_ERR_CARD_CONNECT`     | Using an emulator     |
| 4/5 | `GAMESAVE_ERR_LOAD_DATA_BROKEN` | Unknown     |
| 6   | `GAMESAVE_ERR_LOAD_OLD_VERSION` | Unknown     |
| 7/8 | `GAMESAVE_ERR_SAVE_OTHER`       | Unknown     |

We can set r0 to an ID (i.e., 3 for `GAMESAVE_ERR_CARD_CONNECT`) while paused on `0204bd10` to get an arbitrary error message.
String ID `0x0` results in the following screen:

![image](https://github.com/zurgeg/seatbelt/assets/46549042/501beadc-6d6a-441f-9340-b18de1a06058)

The text in brackets translates to "saving data"

## String ID table
This is a list of string IDs and what they translate to. ~~Kanji characters I can't read (most of them) are replaced with K?~~
Nevermind, I found Japanese OCR.

| String ID                       | Text                                                               | Rough Translation                                                  |
| ------------------------------- | ------------------------------------------------------------------ | ------------------------------------------------------------------ |
| `GAMESAVE_ERR_CARD_CONNECT`     | データを読めませんでした。  電源を切って、DSカードを差し込 み直してください。| Data could not be read. Turn off the power, insert (?) the DS card |               
| `GAMESAVE_ERR_SAVE_OTHER`       | セープデータの保存た失敗しました。                                      | (?) Data saving failed.                                            |
| `GAMESAVE_ERR_LOAD_DATA_BROKEN` | Unknown                                                            |                                                                    |                                         
| `GAMESAVE_ERR_LOAD_OLD_VERSION` | Unknown                                                            |                                                                    |
| `GAMESAVE_ERR_SAVE_OTHER`       | Unknown                                                            |                                                                    |

# The AVN-ZX02i
Denso-ten's flagship product (at the time). Came packaged with Kuruma de DS, and it's the main reason why we're here.

## Protocol
No clue. It must have some sort of indicator, because when a car is started and in bluetooth pairing mode in the vicinity of a DS running UZCJ, UZCJ picks it up, but then errors shortly after.
