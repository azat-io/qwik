## API Report File for "@builder.io/qwik-city"

> Do not edit this file. It is a report generated by [API Extractor](https://api-extractor.com/).

```ts
import type { Action } from '@builder.io/qwik-city';
import type { _deserializeData } from '@builder.io/qwik';
import type { EnvGetter as EnvGetter_2 } from '@builder.io/qwik-city/middleware/request-handler';
import type { FailReturn } from '@builder.io/qwik-city';
import type { Loader as Loader_2 } from '@builder.io/qwik-city';
import type { QwikCityPlan } from '@builder.io/qwik-city';
import type { QwikIntrinsicElements } from '@builder.io/qwik';
import type { Render } from '@builder.io/qwik/server';
import type { RenderOptions } from '@builder.io/qwik/server';
import type { RequestEvent as RequestEvent_2 } from '@builder.io/qwik-city';
import type { RequestHandler as RequestHandler_2 } from '@builder.io/qwik-city/middleware/request-handler';
import type { ResolveSyncValue as ResolveSyncValue_2 } from '@builder.io/qwik-city/middleware/request-handler';
import type { _serializeData } from '@builder.io/qwik';
import type { ValueOrPromise } from '@builder.io/qwik';
import type { _verifySerializable } from '@builder.io/qwik';

// @public (undocumented)
export class AbortMessage {}

// Warning: (ae-forgotten-export) The symbol "CacheControlOptions" needs to be exported by the entry point index.d.ts
//
// @public (undocumented)
export type CacheControl =
  | CacheControlOptions
  | number
  | 'day'
  | 'week'
  | 'month'
  | 'year'
  | 'no-cache'
  | 'immutable'
  | 'private';

// @public (undocumented)
export interface ClientConn {
  // (undocumented)
  country?: string;
  // (undocumented)
  ip?: string;
}

// @public (undocumented)
export interface Cookie {
  append(name: string, value: string | number | Record<string, any>, options?: CookieOptions): void;
  delete(name: string, options?: Pick<CookieOptions, 'path' | 'domain' | 'sameSite'>): void;
  get(name: string): CookieValue | null;
  getAll(): Record<string, CookieValue>;
  has(name: string): boolean;
  headers(): string[];
  set(name: string, value: string | number | Record<string, any>, options?: CookieOptions): void;
}

// @public
export interface CookieOptions {
  domain?: string;
  expires?: Date | string;
  httpOnly?: boolean;
  maxAge?: number | [number, 'seconds' | 'minutes' | 'hours' | 'days' | 'weeks'];
  path?: string;
  sameSite?: 'strict' | 'lax' | 'none' | 'Strict' | 'Lax' | 'None' | boolean;
  secure?: boolean;
}

// @public (undocumented)
export interface CookieValue {
  // (undocumented)
  json: <T = unknown>() => T;
  // (undocumented)
  number: () => number;
  // (undocumented)
  value: string;
}

// @public (undocumented)
export type DeferReturn<T> = () => Promise<T>;

// @public (undocumented)
export interface EnvGetter {
  // (undocumented)
  get(key: string): string | undefined;
}

// @public (undocumented)
export function getErrorHtml(status: number, e: any): string;

// @public (undocumented)
export const mergeHeadersCookies: (headers: Headers, cookies: Cookie) => Headers;

// @public (undocumented)
export class RedirectMessage extends AbortMessage {}

// @public (undocumented)
export interface RequestEvent<PLATFORM = QwikCityPlatform> extends RequestEventCommon<PLATFORM> {
  readonly exited: boolean;
  readonly getWritableStream: () => WritableStream<Uint8Array>;
  readonly headersSent: boolean;
  readonly next: () => Promise<void>;
}

// @public (undocumented)
export interface RequestEventAction<PLATFORM = QwikCityPlatform>
  extends RequestEventCommon<PLATFORM> {
  // (undocumented)
  fail: <T extends Record<string, any>>(status: number, returnData: T) => FailReturn<T>;
}

// @public (undocumented)
export interface RequestEventBase<PLATFORM = QwikCityPlatform> {
  readonly basePathname: string;
  // Warning: (ae-forgotten-export) The symbol "CacheControlTarget" needs to be exported by the entry point index.d.ts
  readonly cacheControl: (cacheControl: CacheControl, target?: CacheControlTarget) => void;
  readonly clientConn: ClientConn;
  readonly cookie: Cookie;
  readonly env: EnvGetter;
  readonly headers: Headers;
  readonly method: string;
  readonly params: Readonly<Record<string, string>>;
  readonly parseBody: () => Promise<unknown>;
  readonly pathname: string;
  readonly platform: PLATFORM;
  readonly query: URLSearchParams;
  readonly request: Request;
  readonly sharedMap: Map<string, any>;
  readonly signal: AbortSignal;
  readonly url: URL;
}

// @public (undocumented)
export interface RequestEventCommon<PLATFORM = QwikCityPlatform>
  extends RequestEventBase<PLATFORM> {
  // Warning: (ae-forgotten-export) The symbol "ErrorCodes" needs to be exported by the entry point index.d.ts
  // Warning: (ae-forgotten-export) The symbol "ErrorResponse" needs to be exported by the entry point index.d.ts
  readonly error: (statusCode: ErrorCodes, message: string) => ErrorResponse;
  // (undocumented)
  readonly exit: () => AbortMessage;
  readonly html: (statusCode: StatusCodes, html: string) => AbortMessage;
  readonly json: (statusCode: StatusCodes, data: any) => AbortMessage;
  readonly locale: (local?: string) => string;
  // Warning: (ae-forgotten-export) The symbol "RedirectCode" needs to be exported by the entry point index.d.ts
  readonly redirect: (statusCode: RedirectCode, url: string) => RedirectMessage;
  // Warning: (ae-forgotten-export) The symbol "SendMethod" needs to be exported by the entry point index.d.ts
  readonly send: SendMethod;
  // Warning: (ae-forgotten-export) The symbol "StatusCodes" needs to be exported by the entry point index.d.ts
  readonly status: (statusCode?: StatusCodes) => number;
  readonly text: (statusCode: StatusCodes, text: string) => AbortMessage;
}

// @public (undocumented)
export interface RequestEventLoader<PLATFORM = QwikCityPlatform>
  extends RequestEventAction<PLATFORM> {
  // (undocumented)
  defer: <T>(returnData: Promise<T> | (() => Promise<T>)) => DeferReturn<T>;
  // (undocumented)
  resolveValue: ResolveValue;
}

// @public (undocumented)
export type RequestHandler<PLATFORM = QwikCityPlatform> = (
  ev: RequestEvent<PLATFORM>
) => Promise<void> | void;

// Warning: (ae-forgotten-export) The symbol "QwikSerializer" needs to be exported by the entry point index.d.ts
// Warning: (ae-forgotten-export) The symbol "QwikCityRun" needs to be exported by the entry point index.d.ts
//
// @public
export function requestHandler<T = unknown>(
  serverRequestEv: ServerRequestEvent<T>,
  opts: ServerRenderOptions,
  qwikSerializer: QwikSerializer
): Promise<QwikCityRun<T> | null>;

// @public (undocumented)
export interface ResolveSyncValue {
  // (undocumented)
  <T>(loader: Loader_2<T>): Awaited<T> extends () => any ? never : Awaited<T>;
  // (undocumented)
  <T>(action: Action<T>): Awaited<T> | undefined;
}

// @public (undocumented)
export interface ResolveValue {
  // (undocumented)
  <T>(loader: Loader_2<T>): Awaited<T> extends () => any ? never : Promise<T>;
  // (undocumented)
  <T>(action: Action<T>): Promise<T | undefined>;
}

// @public (undocumented)
export class ServerError<T = Record<any, any>> extends Error {
  constructor(status: number, data: T);
  // (undocumented)
  data: T;
  // (undocumented)
  status: number;
}

// @public (undocumented)
export interface ServerRenderOptions extends RenderOptions {
  checkOrigin?: boolean;
  // (undocumented)
  qwikCityPlan: QwikCityPlan;
  // (undocumented)
  render: Render;
}

// @public
export interface ServerRequestEvent<T = unknown> {
  // (undocumented)
  env: EnvGetter;
  // (undocumented)
  getClientConn: () => ClientConn;
  // (undocumented)
  getWritableStream: ServerResponseHandler<T>;
  // (undocumented)
  locale: string | undefined;
  // (undocumented)
  mode: ServerRequestMode;
  // (undocumented)
  platform: QwikCityPlatform;
  // (undocumented)
  request: Request;
  // (undocumented)
  url: URL;
}

// @public (undocumented)
export type ServerRequestMode = 'dev' | 'static' | 'server';

// Warning: (ae-forgotten-export) The symbol "RequestEventInternal" needs to be exported by the entry point index.d.ts
//
// @public (undocumented)
export type ServerResponseHandler<T = any> = (
  status: number,
  headers: Headers,
  cookies: Cookie,
  resolve: (response: T) => void,
  requestEv: RequestEventInternal
) => WritableStream<Uint8Array>;

// @internal (undocumented)
export class _TextEncoderStream_polyfill {
  // (undocumented)
  get [Symbol.toStringTag](): string;
  // (undocumented)
  get encoding(): string;
  // (undocumented)
  get readable(): ReadableStream<Uint8Array>;
  // (undocumented)
  get writable(): WritableStream<string>;
}

// @internal (undocumented)
export class _TextEncoderStream_polyfill2 {
  constructor();
  // (undocumented)
  readable: any;
  // (undocumented)
  writable: any;
  // (undocumented)
  _writer: any;
}

// (No @packageDocumentation comment for this package)
```