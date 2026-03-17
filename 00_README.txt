==============Mục lục/目次/TABLE OF CONTENTS============

A. Tiếng Việt
	I. Khái quát
	II. Cấu trúc
	III. Cách compile
	
B. 日本語
	I. 概要
	II. 本フォルダーの構造成分
	III. 実行方法
	
C. English
	I. Overview
	II. Structure
	III. How to Compile

########################   A. Tiếng Việt   ###################################
I. Khái quát
Đây là mã nguồn cho một số cải tiến trong trò chơi điện tử "Fire Emblem Monshō no Nazo" （ファイアーエムブレム紋章の謎/Mộc đế Chiến kỷ 3）được phát hành cho máy chơi game Nintendō Super Famicom vào năm 1994.
Với mã nguồn này, bạn có thể tự compile Rom gốc (tiếng Nhật) để mở khóa những chức năng cải tiến được mô tả bên dưới chỉ với một cú click chuột.
Mã nguồn này được thiết kế để chạy trên Windows. Nếu muốn chạy trên Mac thì bạn cần phải chạy thông qua WINE hoặc máy ảo.
Những chức năng cải tiến gồm:
a. Nhấn nút Select để avatar nhân vật chuyển động miệng
b. Màu của nhân vật trong trận đấu trùng với màu tóc, màu giáp của avatar nhân vật (sẽ cập nhật sau)

II. Cấu trúc
Folder mã nguồn này gồm những thành phần như bên dưới, không tính file Readme này.
◆01_xkas.exe (tác giả: Byuu): phần mềm biến mã assembly trong các file text thành mã máy rồi chèn chúng vào Rom. 
◆01_run_fe3.bat: file batch của Windows, dùng để gọi xkas. Double click file này để chạy.
◆03_FE3code.txt: file text khai báo cho các file code khác.
Mở/chỉnh sửa nó bằng bất kỳ phần mềm text-editor nào, chẳng hạn như Notepad có sẵn trên Windows.
◆03_kuchipaku.txt: file text khai báo địa chỉ phần chuyển động miệng
◆03_maincode.txt: file text chứa phần code để bổ sung những tính năng kể trên.

Trong folder này không bao gồm Rom. 
Nếu bạn sở hữu băng game một cách hợp pháp thì có thể trích xuất Rom từ băng qua các thiết bị như Super UFO PRO 8.

III. Cách compile

1. Mở file "01_run_fe3.bat" bằng phần mềm Notepad hoặc bất kỳ text-editor nào.
Trong này bạn sẽ thấy những dòng lệnh như bên dưới.

=============Code===============
copy 02_FE3ROM.sfc 02_NewFE3.sfc
01_xkas.exe -o 02_NewFE3.sfc 03_FE3code.txt
pause
================================

Trong đó "02_FE3ROM.sfc" là tên Rom gốc chưa chỉnh sửa, còn "02_NewFE3.sfc" là tên bản sao của Rom gốc.
Bạn có thể đổi tên Rom thành bất cứ tên gì cũng được, miễn là nó khớp với phần khai báo trong file .bat này.
Chúng ta làm việc trên bản sao của Rom để tránh gây ảnh hưởng lên Rom gốc.

2. Đặt Rom gốc (tiếng Nhật) của trò "Fire Emblem Monshō no Nazo" vào folder này.

3. Double-click vào file "01_run_fe3.bat". Lúc này xkas sẽ tạo ta file "02_NewFE3.sfc" (hoặc bất kỳ tên gì, ứng với tên được khai báo ở bước 1).

4. Chạy file "02_NewFE3.sfc" vừa được tạo ra bằng các phần mềm giả lập Super Famicom như BSNES, MESEN, SNES9X,...
Bạn cũng có thể chạy file này trên phần cứng Super Famicom thật hoặc những phần cứng clone khác như SupaBoy, RetroN,...

5. Trong game, khi bật Menu chứa avatar nhân vật (nút X hoặc nút A), nhấn thêm nút Select để nhân vật nhép miệng.
Bạn có thể thay đổi thời gian chờ để khiến nhân vật nhếch mép nhanh hơn hay chậm hơn bằng cách thay đổi giá trị "kuchi_delay" trong file "03_maincode.txt".

Lưu ý: Rom gốc của bạn không được chứa 0x0200 byte header.
Dùng bất cứ Hex-editor nào để kiểm tra. Nếu thấy phần header thì xóa nó đi.

Mã nguồn được chia sẻ miễn phí tại:
https://github.com/stoneboat65816/

########################   B. 日本語   ###################################
I. 概要
これソースコードは、1994年に任天堂の家庭用ゲーム機スーパーファミコン向けに発売された『ファイアーエムブレム 紋章の謎』（通称FE3/FE紋章の謎）になかった機能を導入するためのものです。
対応する機能は下記のとおりです。
①マップ上でユニットキャラにカーソルを合わせてXボタンまたはAボタンで顔グラメニューを開いた時、セレクトボタンを押すことで顔グラの口パクが動くようになる。
②顔グラの色（頭髪や鎧）に合わせて戦闘アニメーションにおけるキャラの配色にする。（近い将来更新予定）
本ソースコードを使用することで、無改造ROM（日本語版）を対象としてワンクリックで上記機能を導入することができます。
このソースコードおよび関連ソフトはWindows上で動作させるよう設計されています。MacOSで実行する場合は、WINEまたは仮想マシンを使用してください。

II. 本フォルダーの構造成分
本ソースコードフォルダーには、本Readmeファイルを除き、以下の内容が含まれています。
■01_xkas.exe（作者：Byuu氏）：テキストファイル内のアセンブリコードを機械語へ変換し、ROMへ挿入するソフトウェアです。
■01_run_fe3.bat：Windows用のバッチファイルで、xkasを呼び出すために使用します。本ファイルをダブルクリックすることで実行できます。
■01_enable_debug_room.txt：デバッグルーム機能を解放するためのコードを収録したファイルです。
■03_FE3code.txt: コード全体を総括するテキスト。
Windowsに搭載されているNotepadなど、任意のテキストエディタで開いたり編集したりできます。
■03_kuchipaku.txt: 顔グラの口パク関数を管理するアドレス。
■03_maincode.txt: 上記機能を導入するためのアセンブリコード。

本フォルダーにはROMファイルは含まれていません。
ゲームカセットを所有している場合、Super UFO PRO 8などの吸出し器を使用することでカセットからROMを抽出することが可能です。

III. 実行方法
1. 「01_run_fe3.bat」ファイルを、Notepadまたは任意のテキストエディタで開いてください。
ファイル内には、以下のようなコマンド行が記載されています。
=============Code===============
copy 02_FE3ROM.sfc 02_NewFE3.sfc
01_xkas.exe -o 02_NewFE3.sfc 03_FE3code.txt
pause
================================
ここで、「02_FE3ROM.sfc」は無改造ROMのファイル名で、「02_NewFE3.sfc」はそのコピーのファイル名です。
ROMのファイル名は任意の名称に変更可能ですが、その場合は本.batファイル内で指定されている名称と一致させる必要があります。
無改造ROMに影響を与えないよう、本作業は必ずそのコピーを対象にして行ってください。

2 .無改造ROMの日本語版『ファイアーエムブレム 紋章の謎』を本フォルダー内に置いてください。

3. 「01_run_fe3.bat」をダブルクリックします。
すると、xkasにより「02_NewFE3.sfc」（または1.で指定した任意のファイル名）が生成されます。

4. 生成された「01_FE3_debug.sfc」を、bsnes、Mesen、Snes9x などのスーパーファミコン用エミュレータでプレイしてください。
また、スーパーファミコン実機や、SupaBoy、Retron などの互換機で動作させることも可能です。

5. ゲーム内でカーソルをユニットに合わせてXボタンまたはAボタンで顔グラメニューを開きます。
この時、セレクトボタンを押せば顔グラの口パクが動きます。
口パクの各段階の待機時間を変更したい場合、「03_maincode.txt」の「kuchi_delay」の値を好きな数値に直してください。


※無改造ROMは、ヘッダー（0x200バイト）のないものでないといけません。スターリング等バイナリエディタでROMを開いてヘッダーの有無を確認できます。ヘッダーが確認された場合、バイナリエディタで削除してください。

このソースコードは下記URLにて無料で提供しております。
https://github.com/stoneboat65816/


########################   C. English   ###################################
I. Overview
This is the source code to implement some features that never been in Fire Emblem: Monshō no Nazo (ファイアーエムブレム紋章の謎/Mystery of the Emblem), released for the Super Famicom back in 1994.
These features including
a. Press Select button to make the avatar move its mouth in X button or A button Menu.
b. Character sprite color in the battle (animation mode) become the same as the avatar's color. (to be implemented soon)

With this source code, you can compile the original Japanese ROM yourself and unlock this feature with just a single click.
This source code is designed to run on Windows. If you’re on a Mac, you’ll need to run it through WINE or a virtual machine.

II. Structure
This source folder includes the following files (not counting this Readme):
■01_xkas.exe (author: Byuu):  This tool assembles the assembly code into machine code and inserts it into the ROM.
■01_run_fe3.bat:A Windows batch file used to run xkas. Just double-click this file to execute it.
■03_FE3code.txt: This file contains general information about other assembly code files.
You can open and edit it with any text editor, like the built-in Notepad on Windows.
■03_kuchipaku.txt: This text file contains the address for mouth movement function.
■03_maincode.txt: The main code to enable above features.

The ROM file itself is not included in this folder.
If you legally own the original game cartridge, you can dump the ROM using devices such as the Super UFO PRO 8.

III. How to Compile

1. Open the file "01_run_fe3.bat" using Notepad or any text editor.
Inside, you’ll see lines of code like the ones below.

=============Code===============
copy 02_FE3ROM.sfc 02_NewFE3.sfc
01_xkas.exe -o 02_NewFE3.sfc 03_FE3code.txt
pause
================================
In that file, "01_FE3.sfc" is the name of the original, unmodified ROM, and "02_NewFE3.sfc" is the name of the duplicated ROM that will be patched.
You can rename the ROM to anything you like, as long as it matches what’s written in the .bat file.
We’re working on a copy of the ROM to make sure the original file stays untouched.

2. Place the original Japanese ROM of Fire Emblem: Monshō no Nazo into this folder.

3. Double-click "01_run_fe3.bat".
xkas will then generate a new file called "02_NewFE3.sfc" (or whatever name you specified in step 1).

4. Run the newly created ROM file "02_NewFE3.sfc" using a Super Famicom emulator such as bsnes, Mesen, or SNES9x.
You can also run it on real Super Famicom hardware or compatible clone systems like SupaBoy or RetroN.

5. In the game, after opening the avatar menu by pressing X button or A button, you can press Select button to make the mouth move.
You can modify the delay time by changing "kuchi_delay" value inside "03_maincode.txt".

Note: the untouched ROM must be a headerless one. You can open the ROM using any Hex-editor to comfirm whether it has 0x200 bytes header or not.
If it does, you must delete this header using the Hex-editor.

The source code is available for free at:
https://github.com/stoneboat65816/