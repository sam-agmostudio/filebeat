# filebeat

#### 介绍
python 项目使用filebeat

#### 示例
    import filebeat
    
    # 加载配置，
    # is_linux=True 使用Linux版的filebeat
    # is_linux=False 使用Mac版的filebeat
    fb = filebeat.load_config('filebeat.yml', is_linux=False)
    
    # 运行
    fb.run()


#### filebeat.yml 示例
    filebeat.inputs:
    - type: filestream
      paths:
        - /log/xx.log**
      parsers:
        - ndjson:
            keys_under_root: true
            overwrite_keys: true
            add_error_key: true
            expand_keys: true

    output.logstash:
      # Boolean flag to enable or disable the output module.
      enabled: true
    
      # The Logstash hosts
      hosts: ["0.0.0.0:5144"]


