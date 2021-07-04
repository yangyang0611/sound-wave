# sound-wave
![]https://imgur.com/a/nrMXdrf
        **Figure 1**
我是以個人歌聲下去錄製歌曲——《刻在你心底的名字》，在 command line 輸入
sound(y,fs)就可以播放了 XDD。
• Figure1 代表聲音的震蕩幅度，一開始沒有聲音震蕩波係數為 0，之後會根據音頻高
低在 0.15 到 -0.15 之間震動，中間震蕩波回到係數 0 就是換氣的部分。
• 我在程式碼裏設定 T = 60, 代表整段音頻的 physical connection 為 60 seconds。
• yn – y(:,2) ：代表取資料 y 裏的 col2 的值做圖
• N ： 音樂總長度
• Xn：總時間長度*點的個數/yn 長度
• Plot(xn, yn)：做出以上圖像（Figure 1）


       **Figure 2**
• 由於是人聲，所以 sample rate 設定 44100，間隔 delta_t 0.2 為一格單位
• 記得要把 z = []，把之前參數的記憶體清空
• 接著 for loop 從 1 到長度 length(t) – 1，yt 取 xn 在 t(j)與 t(j+1)的範圍，并用 Nt 來記
錄長度 yt
• Tmax = Nt/SampleRate 是爲了取得傅里葉轉化的后的時間，呼叫 matlat 内建的 fft 函
數做分析
• 人聲的 BandMax 設定成 1500Hz
• k = 1: (BandMax*Tmax) 是爲了采樣 N/2，換算一下得到 Hz 係數
• z(: , j) = abs(c(k+1)) / (N/2))，意思就是 c(1) = a0*N， c(2) = (a1-ib1) * N/2 …
• 使用 matlab 内建 bar(Hz,z)可以畫出 Hz 對 z 的圖（如 figure2）
• 結束 for loop


      **Figure 3**
• surf(t(1:end-1), Hz, z) 创建一个三维曲面图，它是一个具有实色边和实色面的三维曲
面。该函数将矩阵 z 中的值绘制为由 t(1:end-1) 和 Hz 定义的 t(1:end-1)-Hz 平面中
的网格上方的高度。曲面的颜色根据 z 指定的高度而变化。
• view(2)用 2 維作圖
• label(x), label(y) 為 x & y axis 加上名稱
• 再把網格 shading 掉，比較容易辨識圖形
• Colorbar 用來显示当前颜色图并指示数据值到颜色图的映射
