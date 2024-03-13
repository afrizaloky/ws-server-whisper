

git clone https://github.com/ammarfaizi2/ws-server-whisper.git;

cd ws-server-whisper;

bash ./models/download-ggml-model.sh base.en;

make -j$(nproc);

./ws-server -m ./models/ggml-base.en.bin -t 8;



# How to build using CMake
1. cmake -B build
2. cmake --build build -- -j 12
