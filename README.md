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
