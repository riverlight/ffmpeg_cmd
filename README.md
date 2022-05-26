# ffmpeg_cmd
常见的 ffmpeg 命令

#### 观看 yuv420_bit10 的文件
`
-> ffplay -f rawvideo -video_size 2560*1600 -pixel_format yuv420p10le SteamLocomotiveTrain_2560x1600_60_10bit_crop.yuv
`
#### 把 yuv420 文件缩放 0.5 并转码
`
-> ffmpeg -f rawvideo -framerate 25 -video_size 3840x1600 -pix_fmt yuv420p -i ./4k_src\eternals_3840x1600.yuv -vf scale=iw*0.5:-1 -sws_flags bicubic -y -vcodec h264 -crf 18 ./4k_src\eternals_1920x800.mp4
`
#### 把 rgb24 raw 文件转成 png
`
-> ffmpeg -f rawvideo -video_size 128*128 -pixel_format rgb24 -i t1.enc -y t1.png
`

#### 计算psnr
`
-> ffmpeg -i arcane_1920x1080_src.mp4 -i arcane_1920x1080_fsr.mp4 -lavfi psnr="stats_file=arvane-fsr.log" -f null -
`

#### 10bit hevc 转码
`
-> ffmpeg -r 30 -s 2560x1600 -pix_fmt yuv420p10le -i testset-yuv\SteamLocomotiveTrain_2560x1600_60_10bit_crop.yuv -b:v 100M -c:v libx265 -crf 22 -x265-params "colorprim=bt2020:transfer=smpte2084:colormatrix=bt2020nc" -an -y -r 30 SteamLocomotiveTrain_hdr.mp4
`

#### 10bit hevc hdr 转码
`
-> ffmpeg -r 30 -s 2560x1600 -pix_fmt yuv420p10le -i testset-yuv\SteamLocomotiveTrain_2560x1600_60_10bit_crop.yuv -r 60 -crf 22 -c:v libx265 -x265-params "colorprim=bt2020:transfer=smpte2084:colormatrix=bt2020nc:master-display=G(13250,34500)B(7500,3000)R(34000,16000)WP(15635,16450)L(10000000,1):max-cll=1000,400:min-luma=0.001:max-luma=4000" -y Morocco_HDR.mp4
`
