# lucne-reader-open-util
多线程环境下用lucene搜索共享同一个reader类

/**
	 * 最大的reader数量，有多少个文件夹就会有多少个reader
	 */
	private final static int MAX_READER = 5; 决定最多能打开的lucene索引文件夹数量

/**
	 * 一个reader同时被使用最大线程数量
	 */
	private final static int MAX_USE_NUM = 100; 一个已经打开的reader能同时被多少个线程使用

在使用时根据自己的情况设置以上两个值，每次需要一个reader时调用 LuceneOpenReaderUtil.getReader(directoryPath),其中directoryPath是索引的文件夹，使用完需要使用 LuceneOpenReaderUtil.close(directoryPath) 归还该reader，否则会造成该reader永远不能close，最后内存溢出。
