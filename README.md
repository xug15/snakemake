# snakemake

snakemake是一个用来编写任务流程的工具，用python编写的，因此其执行的流程脚本也比较通俗易懂，易于理解。

## 一、从一个简单的例子开始
**1、安装snakemake**
安装snakemake的方法有多种，snakemake官方推荐的是conda，安装方法如下：
```sh
conda install -c bioconda snakemake
```
## 2、一个简单的snakemake脚本
虽然snakemake广泛的应用于生物信息方面的流程编写，但是snakemake的应用并不局限于编写生物信息学的流程，这里以一个简单的合并文件的例子开始介绍snakemake的简单使用。
*首先我们建立两个文件*
```sh
$ echo "Here is hello." > hello.txt
$ echo "Here is world." > world.txt
```

**接下来开始编写我们的Snakefile**
```sh
rule concat:  # 这里的rule可视为snakemake定义的关键字，concat使我们自定义的这一步任务的名称
    input:   # input同样是snakemake的关键字，定义了在这个任务中的输入文件 
        expand("{file}.txt", file=["hello", "world"]) #expand是一个snakemake定义的替换命令
    output:   # output也是snakemake的关键字，定义输出结果的保存文件
        "merged.txt"
    shell:  # 这里表示我们下面的命令将在命令行中执行
        "cat {input} > {output}"
```
**最后就可以在Snakefile的路径执行snakemake命令即可**
```sh
$ snakemake
$ cat merge.txt
Here is hello.
Here is world.
```
在上面的Snakefile脚本中，rule、input、output、shell、expand均为snakemake中的关键字或者命令。同时Snakefile中的每一个rule其实都可以看作是一个简单的shell脚本，通过Snakefile将多个rule组织在一起并按照我们定义的顺序来执行。另外，在output中的结果文件可以是未存在目录中的文件,这时会自动创建不存在的目录。
## 二、snakemake中的一些命令与规则
* 1、rule
rule是Snakefile中最主要的部分。如上面的例子所说，每一个rule定义了一系列pipe中的一步，每一个rule都可以当作一个shell脚本来处理，一般主要包括input、output、shell3个部分。同时还有许多上面没有列出来的用法：

rule all。不同于其他的rule，在rule all里面一般不会去定义要执行的命令，他一般用来定义最后的输出结果文件。除了rule all中定义的文件外最后输出结果不会保存任何中间文件。例如将上面的脚本改成如下文件则没有输出结果：

```py
rule all:
    input:
         #"merged.txt"  取消注释后，则能正常输出文件
rule concat:
    input:
        expand("{file}.txt", file=["hello", "world"])
    output:
        "merge.txt"
    shell:
        "cat {input} > {output}"
```


* wildcards。用来获取通配符匹配到的部分，例如对于通配符"{dataset}/file.{group}.txt"匹配到文件101/file.A.txt，则{wildcards.dataset}就是101，{wildcards.group}就是A。

* threads。通过在rule里面指定threads参数来指定分配给程序的线程数，egthreads: 8。

* resources。可用来指定程序运行的内存，eg. resources: mem_mb=800。

* message。使用message参数可以指定每运行到一个rule时，在终端中给出提示信息，eg.message: "starting mapping ..."。

* priority。可用来指定程序运行的优先级，默认为0，eg.priority: 20。

* log。用来指定生成的日志文件，eg.log: "logs/concat.log"。

* params。指定程序运行的参数，eg.params: cat="-n",调用方法为{params.cat}。

* run。在run的缩进区域里面可以输入并执行python代码。

* scripts。用来执行指定脚本，eg.scripts: "rm_dup.py"


* temp。通过temp方法可以在所有rule运行完后删除指定的中间文件，eg.output: temp("f1.bam")。

* protected。用来指定某些中间文件是需要保留的，eg.output: protected("f1.bam")。

* ancient。重复运行执行某个Snakefile时，snakemake会通过比较输入文件的时间戳是否更改(比原来的新)来决定是否重新执行程序生成文件，使用ancient方法可以强制使得结果文件一旦生成就不会再次重新生成覆盖，即便输入文件时间戳已经更新，eg.input: ancient("f1.fastq")。
* Rule Dependencies。可通过快捷方式指定前一个rule的输出文件为此rule的输入文件：
```py
rule a:
    input:  "path/to/input"
    output: "path/to/output"
    shell:  ...

rule b:
    input:  rules.a.output   #直接通过rules.a.output 指定rule a的输出
    output: "path/to/output/of/b"
    shell:  ...
```


report。使用snakemake定义的report函数可以方便的将结果嵌入到一个HTML文件中进行查看。

**2. configuration**
每计算一次数据都要重写一次Snakefile有时可能会显得有些繁琐，我们可以将那些改动写入配置文件，使用相同流程计算时，将输入文件的文件名写入配置文件然后通过Snakefile读入即可。
配置文件有两种书写格式——json和yaml。在Snakefile中读入配置文件使用如下方式：
```sh
configfile: "path/to/config.json" 
configfile: "path/to/config.yaml"
```

# 也可直接在执行snakemake命令时指定配置
```sh
$ snakemake --config yourparam=1.5
```
在shell命令中直接调用config文件中的内容的话，不需要引号，如config[a]而不是config["a"]。
集群计算配置
## 三、snakemake的执行
一般讲所有的参数配置写入Snakefile后直接在Snakefile所在路径执行snakemake命令即可开始执行流程任务。一些常用的参数：
```sh
--snakefile, -s 指定Snakefile，否则是当前目录下的Snakefile
--dryrun, -n  不真正执行，一般用来查看Snakefile是否有错
--printshellcmds, -p   输出要执行的shell命令
--reason, -r  输出每条rule执行的原因,默认FALSE
--cores, --jobs, -j  指定运行的核数，若不指定，则使用最大的核数
--force, -f 重新运行第一条rule或指定的rule
--forceall, -F 重新运行所有的rule，不管是否已经有输出结果
--forcerun, -R 重新执行Snakefile，当更新了rule时候使用此命令
```

**一些可视化命令**
```sh
$ snakemake --dag | dot -Tpdf > dag.pdf
```

**集群投递**
```sh
snakemake --cluster "qsub -V -cwd -q 节点队列" -j 10
# --cluster /-c CMD: 集群运行指令
# qusb -V -cwd -q， 表示输出当前环境变量(-V),在当前目录下运行(-cwd), 投递到指定的队列(-q), 如果不指定则使用任何可用队列
# --local-cores N: 在每个集群中最多并行N核
# --cluster-config/-u FILE: 集群配置文件
```

作者：To_2020_1_4
链接：https://www.jianshu.com/p/14b9eccc0c0e
来源：简书
简书著作权归作者所有，任何形式的转载都请联系作者获得授权并注明出处。




