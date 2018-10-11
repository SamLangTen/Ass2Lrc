# ASS2LRC
## Introduction
This script can convert ASS subtitle file to common LRC lryics file.

    usage: python .\ass2lrc.py [--help] -i <inputfile> -o <outputfile> [-t mileseconds] [-s stylename] [-c|-a] [-f [mm:ss.xx]]
    
    -i --input              An ASS filename which will be converted to lrc
    -o --output             A LRC filename where the convered text will be stored
    -t --split_timespan     A new blank line will be added if the start time of two between dialogues greater than this argument, default is 1000ms
    -s --convert_styles     A filter to decide which style of dialogue in ASS should be converted into LRC file
    -c --compact            Combine timestamp of dialogues with same text, not supported by all player
    -a --accurate           Convert Karaoke-tag of ASS file to accurate word-by-word timestamp, not supported by all players. Not compatible with compact option
    -f --accurate_format    Used with accurate option, to set format of accurate word-by-word timestamp since every player may have its own accurate timestamp

Since LRC file does not support ending timestamp, some lryics followed with a long period time of music will be "frozen". This script can add a new blank lyrics whose start timestamp is ending timestamp of the former lyrics. If timespan between the former ending time and the latter start time is greater than option split_timespan, a new blank line will be added.

Some ASS files may contain more than one kind of style because different style represents different kind of subtitle. Convert Styles setting can filter the dialogues with style which you want to convert into LRC dialogues.

## Examples
The original ASS file

    [Script Info]
    ; Script generated by Aegisub 3.2.2
    ; http://www.aegisub.org/
    Title: Default Aegisub file
    ScriptType: v4.00+
    WrapStyle: 0
    ScaledBorderAndShadow: yes
    YCbCr Matrix: None
    PlayResX: 640
    PlayResY: 480

    [V4+ Styles]
    Format: Name, Fontname, Fontsize, PrimaryColour, SecondaryColour, OutlineColour, BackColour, Bold, Italic, Underline, StrikeOut, ScaleX, ScaleY, Spacing, Angle, BorderStyle, Outline, Shadow, Alignment, MarginL, MarginR, MarginV, Encoding
    Style: Default,Aerial,40,&H00FFFFFF,&H000000FF,&H00000000,&H00000000,-1,0,0,0,100,100,0,0,1,1,0,2,10,10,10,1
    Style: InfoStyle,Aerial,40,&H00FFFFFF,&H000000FF,&H00000000,&H00000000,-1,0,0,0,100,100,0,0,1,1,0,2,10,10,10,1

    [Events]
    Format: Layer, Start, End, Style, Name, MarginL, MarginR, MarginV, Effect, Text
    Dialogue: 0,0:00:00.62,0:00:07.52,Default,,0,0,0,,{\K72}高{\K106}く{\K69}高{\K112}く{\K0} {\K43}こ{\K24}の{\K26}手{\K44}を{\K24}伸{\K42}ば{\K42}し{\K86}て
    Dialogue: 0,0:00:07.80,0:00:17.04,Default,,0,0,0,,{\K44}き{\K22}っ{\K114}と{\K0} {\K38}き{\K24}っ{\K53}と{\K10} {\K22}っ{\K48}て{\K19}も{\K15}う{\K48}一{\K37}度{\K83}愿う{\K35}か{\K312}ら
    Dialogue: 0,0:00:28.86,0:00:32.06,Default,,0,0,0,,{\K21}と{\K29}め{\K18}ど{\K27}な{\K19}い{\K67}想{\K16}い{\K123}は
    Dialogue: 0,0:00:32.46,0:00:35.62,Default,,0,0,0,,{\K45}日{\K45}常{\K18}に{\K24}饮{\K30}ま{\K30}れ{\K124}て
    Dialogue: 0,0:00:36.08,0:00:42.76,Default,,0,0,0,,{\K22}揺{\K22}ら{\K19}め{\K23}き{\K23}な{\K43}が{\K43}ら{\K43}ま{\K43}た{\K96}形{\K65}を{\K42}変{\K43}え{\K31}て{\K37}い{\K73}った
    Dialogue: 0,0:00:43.04,0:00:46.58,Default,,0,0,0,,{\K38}今{\K14}さ{\K13}ら{\K38}も{\K40}う{\K39}遅{\K40}い{\K31}か{\K101}な
    Dialogue: 0,0:00:46.80,0:00:50.16,Default,,0,0,0,,{\K12}返{\K13}事{\K14}の{\K27}な{\K34}い{\K25}自{\K50}问{\K28}自{\K133}答
    Dialogue: 0,0:00:50.26,0:00:53.16,Default,,0,0,0,,{\K20}す{\K14}べ{\K11}て{\K10}は{\K22}そ{\K43}う{\K24}自{\K36}分{\K33}次{\K77}第
    Dialogue: 0,0:00:53.16,0:00:57.66,Default,,0,0,0,,{\K35}终{\K75}わ{\K16}り{\K64}も{\K65}始{\K26}ま{\K42}り{\K127}も{\K0}
    Dialogue: 0,0:00:57.98,0:01:04.94,Default,,0,0,0,,{\K67}高{\K104}く{\K72}高{\K104}く{\K29} {\K28}こ{\K22}の{\K25}手{\K35}を{\K29}伸{\K35}ば{\K48}し{\K98}て
    Dialogue: 0,0:01:04.94,0:01:12.08,Default,,0,0,0,,{\K52}优{\K45}し{\K66}い{\K101}光{\K115}を{\K41}目{\K24}指{\K23}し{\K43}て{\K30}羽{\K40}ば{\K40}た{\K21}く{\K73}よ
    Dialogue: 0,0:01:12.08,0:01:19.16,Default,,0,0,0,,{\K100}心{\K74}に{\K54}灯{\K43}し{\K105}た{\K68}情{\K69}热{\K28}を{\K42}抱{\K46}い{\K79}て
    Dialogue: 0,0:01:19.16,0:01:27.44,Default,,0,0,0,,{\K66}き{\K134}っと {\K59}き{\K116}っと {\K40}って{\K32}もう{\K38}一{\K41}度{\K82}愿う{\K27}か{\K193}ら
    Dialogue: 0,0:00:18.44,0:00:20.44,Default,,0,0,0,,春奈るな - Overfly （TV size ver.）
    Dialogue: 0,0:00:20.44,0:00:22.44,InfoStyle,,0,0,0,,Author：Saku
    Dialogue: 0,0:00:22.44,0:00:24.44,InfoStyle,,0,0,0,,Composer：Saku
    Dialogue: 0,0:00:24.44,0:00:26.44,InfoStyle,,0,0,0,,Lyrics by：Samersions

### Convert Directly
    python ass2lrc.py -i input.ass -o output.lrc

Result

    [00:00.62]高く高く この手を伸ばして
    [00:07.80]きっと きっと ってもう一度愿うから
    [00:17.04]
    [00:18.44]春奈るな - Overfly （TV size ver.）
    [00:20.44]Author：Saku
    [00:22.44]Composer：Saku
    [00:24.44]Lyrics by：Samersions
    [00:26.44]
    [00:28.86]とめどない想いは
    [00:32.46]日常に饮まれて
    [00:36.08]揺らめきながらまた形を変えていった
    [00:43.04]今さらもう遅いかな
    [00:46.80]返事のない自问自答
    [00:50.26]すべてはそう自分次第
    [00:53.16]终わりも始まりも
    [00:57.98]高く高く この手を伸ばして
    [01:04.94]优しい光を目指して羽ばたくよ
    [01:12.08]心に灯した情热を抱いて
    [01:19.16]きっと きっと ってもう一度愿うから
    [01:27.44]

### Convert with 10ms splitting timespan, selected Default style
    python ass2lrc.py -i input.ass -o output.lrc -s Default -t 10

Result

    [00:00.62]高く高く この手を伸ばして
    [00:07.52]
    [00:07.80]きっと きっと ってもう一度愿うから
    [00:17.04]
    [00:18.44]春奈るな - Overfly （TV size ver.）
    [00:20.44]
    [00:28.86]とめどない想いは
    [00:32.06]
    [00:32.46]日常に饮まれて
    [00:35.62]
    [00:36.08]揺らめきながらまた形を変えていった
    [00:42.76]
    [00:43.04]今さらもう遅いかな
    [00:46.58]
    [00:46.80]返事のない自问自答
    [00:50.16]
    [00:50.26]すべてはそう自分次第
    [00:53.16]终わりも始まりも
    [00:57.66]
    [00:57.98]高く高く この手を伸ばして
    [01:04.94]优しい光を目指して羽ばたくよ
    [01:12.08]心に灯した情热を抱いて
    [01:19.16]きっと きっと ってもう一度愿うから
    [01:27.44]

### Convert with compact mode

    python ass2lrc.py -i input.ass -o output.lrc -c

Result

    [00:00.62][00:57.98]高く高く この手を伸ばして
    [00:07.80][01:19.16]きっと きっと ってもう一度愿うから
    [00:18.44]春奈るな - Overfly （TV size ver.）
    [00:20.44]Author：Saku
    [00:22.44]Composer：Saku
    [00:24.44]Lyrics by：Samersions
    [00:28.86]とめどない想いは
    [00:32.46]日常に饮まれて
    [00:36.08]揺らめきながらまた形を変えていった
    [00:43.04]今さらもう遅いかな
    [00:46.80]返事のない自问自答
    [00:50.26]すべてはそう自分次第
    [00:53.16]终わりも始まりも
    [01:04.94]优しい光を目指して羽ばたくよ
    [01:12.08]心に灯した情热を抱いて
    [00:17.04][00:26.44][01:27.44] 
    
### Convert with accurate mode, accurate format is "\<mm:ss.xx\>"
    python ass2lrc.py -i input.ass -o output.lrc -a -f <mm:ss.xx> 

Result

    [00:00.62]<00:00.62>高<00:01.34>く<00:02.40>高<00:03.09>く<00:04.21> <00:04.21>こ<00:04.64>の<00:04.88>手<00:05.14>を<00:05.58>伸<00:05.82>ば<00:06.24>し<00:06.66>て
    [00:07.80]<00:07.80>き<00:08.24>っ<00:08.46>と<00:09.60> <00:09.60>き<00:09.98>っ<00:10.22>と<00:10.75> <00:10.85>っ<00:11.07>て<00:11.55>も<00:11.74>う<00:11.89>一<00:12.37>度<00:12.74>愿う<00:13.57>か<00:13.92>ら
    [00:17.04]
    [00:18.44]春奈るな - Overfly （TV size ver.）
    [00:20.44]Author：Saku
    [00:22.44]Composer：Saku
    [00:24.44]Lyrics by：Samersions
    [00:26.44]
    [00:28.86]<00:28.86>と<00:29.07>め<00:29.36>ど<00:29.54>な<00:29.81>い<00:30.00>想<00:30.67>い<00:30.83>は
    [00:32.46]<00:32.46>日<00:32.91>常<00:33.36>に<00:33.54>饮<00:33.78>ま<00:34.08>れ<00:34.38>て
    [00:36.08]<00:36.08>揺<00:36.30>ら<00:36.52>め<00:36.71>き<00:36.94>な<00:37.17>が<00:37.60>ら<00:38.03>ま<00:38.46>た<00:38.89>形<00:39.85>を<00:40.50>変<00:40.92>え<00:41.35>て<00:41.66>い<00:42.03>った
    [00:43.04]<00:43.04>今<00:43.42>さ<00:43.56>ら<00:43.69>も<00:44.07>う<00:44.47>遅<00:44.86>い<00:45.26>か<00:45.57>な
    [00:46.80]<00:46.80>返<00:46.92>事<00:47.05>の<00:47.19>な<00:47.46>い<00:47.80>自<00:48.05>问<00:48.55>自<00:48.83>答
    [00:50.26]<00:50.26>す<00:50.46>べ<00:50.60>て<00:50.71>は<00:50.81>そ<00:51.03>う<00:51.46>自<00:51.70>分<00:52.06>次<00:52.39>第
    [00:53.16]<00:53.16>终<00:53.51>わ<00:54.26>り<00:54.42>も<00:55.06>始<00:55.71>ま<00:55.97>り<00:56.39>も<00:57.66>
    [00:57.98]<00:57.98>高<00:58.65>く<00:59.69>高<01:00.41>く<01:01.45> <01:01.74>こ<01:02.02>の<01:02.24>手<01:02.49>を<01:02.84>伸<01:03.13>ば<01:03.48>し<01:03.96>て
    [01:04.94]<01:04.94>优<01:05.46>し<01:05.91>い<01:06.57>光<01:07.58>を<01:08.73>目<01:09.14>指<01:09.38>し<01:09.61>て<01:10.04>羽<01:10.34>ば<01:10.74>た<01:11.14>く<01:11.35>よ
    [01:12.08]<01:12.08>心<01:13.08>に<01:13.82>灯<01:14.36>し<01:14.79>た<01:15.84>情<01:16.52>热<01:17.21>を<01:17.49>抱<01:17.91>い<01:18.37>て
    [01:19.16]<01:19.16>き<01:19.82>っと <01:21.16>き<01:21.75>っと <01:22.91>って<01:23.31>もう<01:23.63>一<01:24.01>度<01:24.42>愿う<01:25.24>か<01:25.51>ら
    [01:27.44]
