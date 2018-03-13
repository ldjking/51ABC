a1_map  

a2_account    账户表
	id 			账户主键
	nickname	昵称
	create_time	创建时间
	ref_metakey	创世交易
	deal_key	交易密钥
	wit_key		见证密钥
	reset_key_cipher1	重置密钥加密串1
	reset_key_cipher2	重置密钥加密串2   公开后可重置deal_key wit_key
	realname	实名
	idcard_short	身份证尾号
	idcard_cipher	身份证加密密文
	last_update		上次更新时间 一般12小时打包一次
	last_balance	上次更新余额


a3_exchange   	交换记录表  1对1交易
	metakey 		唯一主键
	type			交易类型   付款  收款  退款  预付款  预收款  退预付款  实付款  实收款  退实付款
							   加入合约   
	a           	操作人
	b_type	    	b的类型，交易对手，智能合约
	b           	交易对手，如果是智能合约，则最终由智能合约分配
	amt         	金额
	vote			加入合约时可以vote  投票
	occur_time  	发起时间
	ref_metakey		引用交易记录（上次交易的key）
	a_pubkey    	操作人公钥
	a_hmacstr   	操作人hmac的随机串
	c           	操作人后续的保险箱
	msg         	交易留言记录
	sign        	操作人签名
	ref_ex_list 	引用交易，最多100个，逐项hash 并签名

a4_contract     智能合约表   两种  定向合约  开放合约  
    metakey
    type            交易类型  build定向合约    build开放合约
    a               操作人
    b_list          交易对手
    amt_list        每个交易对手的加入金额
    amt_min         开放合约的最小金额
    amt_max         开放合约的最大金额
    result_commit_method 定向合约的结果表决方法  表决60%  100%一致 裁判  裁判+表决
    result_list		结果清单
    assign_list		不同结果下的分配规则
    fail_days		结束时间
    no_result_assign 	无一致结果分配规则
    occur_time  	发起时间
	ref_metakey		引用交易记录（上次交易的key）
	a_pubkey    	操作人公钥
	a_hmacstr   	操作人hmac的随机串
	c           	操作人后续的保险箱
	msg         	交易留言记录
	sign        	操作人签名



a4_witness    见证表
	witkey 			见证主键
	metakey 		交易主键  也可能是合约主键
	key_info		交易关键信息
	vote_cipher1	加密表决合约加密值1
	vote_cipher2	加密表决合约加密值2
	vote            公开表决
	a 				见证人
	a_pubkey		见证人公钥
	a_hmacstr   	见证人hmac的随机串
	a_ref_witkey	上次见证记录
	wittime			见证时间
	c 				见证后新的保险箱
	sign 			见证签名
