# Rule Merger

1. 安装 `python` 以及必要依赖
   ```shell
   python -m pip install --upgrade pip
   pip install -r requirements.txt
   ```

2. 编辑 `config.yaml` 以列表形式定义需要生成的文件以及其上游规则，基本格式与 Mihomo rule-providers 一致

    ```yaml
      - path: output/lan@ip.mrs
        format: mrs
        behavior: ipcidr
        upstream:
      
          local_lan:
            type: file
            path: local/lan@ip.yaml
            format: yaml
            behavior: classical
      
      - path: output/lan.mrs
        format: mrs
        behavior: domain
        upstream:
      
          skk_lan:
            type: http
            url: "https://example.dev/Clash/non_ip/lan.txt"
            format: text
            behavior: classical
    ```

3. 配置 Mihomo 路径 (使用 `mrs` 格式必要条件)   
   - 修改 `rule_merger.py` 的 `MIHOMO_PATH` 字段  
   - 或将 `mihomo` 可执行文件加入 `/usr/local/bin/` 或 `$PATH` 环境变量中

4. 执行脚本

   ```shell
   python rule_merger.py
   ```
