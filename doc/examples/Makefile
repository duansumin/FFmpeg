# use pkg-config for getting CFLAGS and LDLIBS
FFMPEG_LIBS=    libavdevice                        \
                libavformat                        \
                libavfilter                        \
                libavcodec                         \
                libswresample                      \
                libswscale                         \
                libavutil                          \

CFLAGS += -Wall -g
CFLAGS := $(shell pkg-config --cflags $(FFMPEG_LIBS)) $(CFLAGS)
LDLIBS := $(subst SDL,SDL2, $(shell pkg-config --libs $(FFMPEG_LIBS)) $(LDLIBS))

EXAMPLES=       avio_dir_cmd                       \
                avio_reading                       \
                decoding_encoding                  \
                demuxing_decoding                  \
                extract_mvs                        \
                filtering_video                    \
                filtering_audio                    \
                http_multiclient                   \
                metadata                           \
                muxing                             \
                remuxing                           \
                resampling_audio                   \
                scaling_video                      \
                transcode_aac                      \
                transcoding                        \
		simplest_ffmpeg_player			\
		simplest_ffmpeg_player_su		\
		simplest_ffmpeg_decoder_pure		\
		simplest_ffmpeg_decoder			\
		simplest_video_play_sdl2		\
		simplest_ffmpeg_helloworld		\

OBJS=$(addsuffix .o,$(EXAMPLES))

# the following examples make explicit use of the math library
avcodec:           LDLIBS += -lm
decoding_encoding: LDLIBS += -lm
muxing:            LDLIBS += -lm
resampling_audio:  LDLIBS += -lm

.phony: all clean-test clean

all: $(OBJS) $(EXAMPLES)

clean-test:
	$(RM) test*.pgm test.h264 test.mp2 test.sw test.mpg

clean: clean-test
	$(RM) $(EXAMPLES) $(OBJS)
