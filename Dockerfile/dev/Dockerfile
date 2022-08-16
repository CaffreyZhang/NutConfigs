FROM ubuntu:latest
ENV DEBIAN_FRONTED="noninteractive"
ENV CLICOLOR_FORCE=1
ENV COLORTERM="truecolor"
RUN apt update && apt install -y git curl ripgrep autojump vim zsh duf lrzsz exa && rm -rf /var/lib/apt/lists/* && chsh -s /bin/zsh
COPY conf /root/conf
COPY app /root/app
RUN /bin/zsh /root/conf/omzinstall.sh && \
    git clone --depth=1 https://gitee.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k && \
    git clone https://gitee.com/githubClone/zsh-autosuggestions.git ~/.oh-my-zsh/custom/plugins/zsh-autosuggestions && \
    git clone https://gitee.com/mirror-hub/zsh-syntax-highlighting.git ~/.oh-my-zsh/custom/plugins/zsh-syntax-highlighting && \
    mv /root/conf/.zshrc /root/.zshrc && \
    mv /root/conf/.p10k.zsh /root/.p10k.zsh && \
    mkdir -p /root/.config/procs && \
    mv /root/conf/procs.conf /root/.config/procs/config.toml
COPY app /root/app
RUN dpkg -i /root/app/bottom_0.6.8_amd64.deb && \
    dpkg -i /root/app/du-dust_0.8.1_amd64.deb && \
    mv /root/app/procs-v0.13.0-x86_64-linux/procs /usr/local/bin/procs && \
    rm -rf /root/app /root/conf
WORKDIR /root
ENTRYPOINT [ "/bin/zsh" ]